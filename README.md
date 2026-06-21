# cicd-projects

A collection of small CI/CD example projects and templates demonstrating HTML front-ends and Docker-based builds/images.

This repository contains example HTML apps and Dockerfiles you can use to learn and test continuous integration and continuous deployment pipelines (for example, GitHub Actions, GitLab CI, or other CI systems).

## Table of contents

- About
- Repository layout
- Quick start (build & run with Docker)
- Running locally (HTML)
- CI/CD guidance
- Contributing
- License

## About

This repository showcases simple projects that are easy to build, test, and deploy as part of CI/CD pipelines. The codebase is primarily made up of static HTML sites and Dockerfiles that package those sites or related services into containers.

Use these examples as a starting point to learn or prototype automated pipelines: build, test, containerize, and deploy.

## Repository layout

(Adjust paths below to match this repository's structure if needed)

- / - root containing README and project folders
- /examples/html-app - simple static HTML app(s)
- /docker - Dockerfiles and container build examples
- /.github/workflows - GitHub Actions workflow examples (if present)

## Quick start — build & run with Docker

1. Build a Docker image from a Dockerfile in the repo:

   docker build -t cicd-example -f docker/Dockerfile .

2. Run the image locally:

   docker run --rm -p 8080:80 cicd-example

3. Open http://localhost:8080 to view the app.

Replace the Dockerfile path and ports as appropriate for the project you want to run.

## Running locally (HTML)

If the project is a static HTML site, you can preview it locally without Docker:

1. Open the HTML files in a browser from the file system, or serve them with a lightweight server:

   # using Python 3
   python3 -m http.server 8000 --directory examples/html-app

2. Open http://localhost:8000 in your browser.

## CI/CD guidance

These examples are intended to be used with CI/CD pipelines. Typical pipeline steps include:

1. Checkout code
2. Run linters and static checks (for HTML/CSS/JS)
3. Build artifacts (e.g., build frontend, or create Docker images)
4. Run tests (if any)
5. Push container images to a registry (Docker Hub, GitHub Container Registry, etc.)
6. Deploy to an environment (staging/production)

If you use GitHub Actions, place workflow YAML files under `.github/workflows/` and include steps to build and push Docker images, or to deploy static sites to GitHub Pages.

Example minimal GitHub Actions steps for Docker build & push:

- name: Build Docker image
  uses: docker/build-push-action@v4
  with:
    push: true
    tags: user/repo:latest

Adjust to your organization, registry, and authentication method.

## Contributing

Contributions are welcome. Suggestions:

- Add new example projects (small, focused on a specific CI/CD pattern)
- Add GitHub Actions or other pipeline configs demonstrating build/test/deploy
- Improve documentation and step-by-step tutorials

When opening a PR, please include a short description of the example and any instructions needed to run it.

## License

This repository does not include a license file. If you want to allow reuse, add a LICENSE (for example, MIT) and mention it here.
