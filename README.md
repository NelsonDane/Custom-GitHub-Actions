# Cusotm-GitHub-Actions
Personal GitHub Actions for Docker Containers and Code Formatting

## How to use (for future self)

### DockerHub Build and Push
Automatically builds and pushes images to Docker Hub.

Required Inputs:
- `image_name`: (name of image)

Optional Inputs:
- `platforms`: (defaults to `linux/amd64`)
- `image_tag`: (defaults to `latest`)
- `should_push`: (defaults to `false`)

Optional Secrets:
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_PASSWORD`

Minimal Config (Only builds, does not push):
```yaml
jobs:
  call-dockerhub-action:
    uses: NelsonDane/Cusotm-GitHub-Actions/.github/workflows/dockerhub-build-push.yml@main
    with:
      image_name: name of image
```

Example Config:
```yaml
jobs:
  call-dockerhub-action:
    uses: NelsonDane/Cusotm-GitHub-Actions/.github/workflows/dockerhub-build-push.yml@main
    with:
      image_name: name of image
      platforms: (optional, comma-seperated with no spaces)
      image_tag: (optional)
      should_push: (optional)
    secrets:
      DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
      DOCKERHUB_PASSWORD: ${{ secrets.DOCKERHUB_PASSWORD }}
```

### Auto Update Docker Hub README/Description
Automatically updates the Docker Hub README/Description with the contents of the README.md file in the GitHub repo.

Required Inputs:
- `image_name`

Required Secrets:
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_PASSWORD`

Example Config:
```yaml
jobs:
  call-dockerhub-action:
    uses: NelsonDane/Cusotm-GitHub-Actions/.github/workflows/dockerhub-description.yml@main
    with:
      image_name: (name of image)
    secrets:
      DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
      DOCKERHUB_PASSWORD: ${{ secrets.DOCKERHUB_PASSWORD }}
```
