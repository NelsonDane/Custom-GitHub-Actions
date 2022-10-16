# DockerHub-Actions
Peronal GitHub Actions for Docker Hub

## How to use (for future self)

### Auto build and push
Automatically builds and pushes images to Docker Hub.

Required Inputs:
- `dockerhub_repo_name`: (for when it's different than GitHub's repo name)

Optional Inputs:
- `image_tag`: (defaults to `latest`)
- `platforms`: (defaults to `linux/amd64`)

Required Secrets:
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_PASSWORD`

Example Config:
```yaml
jobs:
  call-dockerhub-action:
    uses: NelsonDane/DockerHub-Actions/.github/workflows/dockerhub_build_push.yml@main
    with:
      dockerhub_repo_name: name of repo
      image_tag: (optional)
      platforms: (optional, comma-seperated with no spaces)
    secrets:
      DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
      DOCKERHUB_PASSWORD: ${{ secrets.DOCKERHUB_PASSWORD }}
```

### Auto Update Docker Hub Readme
Automatically updates the Docker Hub readme with the contents of the README.md file in the GitHub repo.

Required Inputs:
- `dockerhub_repo_name`

Required Secrets:
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_PASSWORD`

Example Config:
```yaml
jobs:
  call-dockerhub-action:
    uses: NelsonDane/DockerHub-Actions/.github/workflows/dockerhub-description.yml@main
    with:
      dockerhub_repo_name: name of repo
    secrets:
      DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
      DOCKERHUB_PASSWORD: ${{ secrets.DOCKERHUB_PASSWORD }}
```
