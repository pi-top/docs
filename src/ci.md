# ⚙️ Building And Deploying (CI)

This section outlines how pi-topOS software packages are built and deployed (Continuous Integration).

## Building
All software installed by pi-top onto pi-topOS is provided as Debian packages, and uses standard Debian packaging tools.

Because some of our software requires code to be compiled for Raspberry Pi's ARM architecture, and the fact that most
CI tools do not offer ARM host machines to build on, pi-top packages are built in a Docker container, leveraging Docker's
`buildx` functionality. This allows all packages to be built in an environment that emulates ARM hardware, where needed.
Packages that will work on multiple architectures are built without hardware emulation to speed up builds.

All public GitHub repositories have GitHub Actions for building (and testing, where relevant).

## Deploying
At the moment, pi-top packages are deployed to pi-top's apt repository using a private self-hosted Jenkins instance.
See the future plans below for how we intend to update the deployment flow.

## Future development plans
* Push to apt repositories directly from GitHub repositories
* Build pi-topOS using GitHub Actions
  * Migrate to Docker builds
* Provide repositories for all packages deployed to pi-top's apt repository
  * Import source using `gbp --import-orig`
  * Watch upstream for updates via `debian/watch`
  * Only needs to provide `debian/` and build CI
* Run tests as part of Debian packaging (via `debian/rules`)

## Links
* [deb-build-docker](https://github.com/pi-top/deb-build-docker)
* [test-run-docker](https://github.com/pi-top/test-run-docker)
* [SDK GitHub Actions workflows](https://github.com/pi-top/pi-top-Python-SDK/tree/master/.github/workflows)
