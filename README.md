# Pester Linux Runner

Provides an image to run [Pester](https://github.com/pester/Pester#pester) tests in a Linux container environment.

Other utilities like [curl](https://curl.haxx.se/) and [Docker](https://www.docker.com/) are also bundled with this image.

## Usage

The following command builds the `adminb/pester-runner` image from the [Dockerfile](Dockerfile).

```PowerShell
docker build -t adminb/pester-runner .
```

To run the image use the command below:

```PowerShell
docker run -v /var/run/docker.sock:/var/run/docker.sock -v ${pwd}:/test adminb/pester-runner
```

The `pester-runner` image will run all the tests found in the folder `/test`. The `/test` folder can be mapped as a volume to a local folder or can be populated when creating another image.

For example, running the following [PowerShell](https://github.com/PowerShell/PowerShell#-powershell) command will run any Pester tests found in the current directory and folders that it contains:

```PowerShell
docker run -v /var/run/docker.sock:/var/run/docker.sock -v ${pwd}:/test adminb/pester-runner

Executing all tests in '.'
Tests completed in 0ms
Tests Passed: 0, Failed: 0, Skipped: 0, Pending: 0, Inconclusive: 0
```

In the instance shown above no Pester tests were detected so no activities were actually tested. Add some tests to the current directory or point the `/test` volume mount at a location containing Pester tests and these will be run by the `pester-runner` container.

`Docker` is also available, it can be used to mount a volume sharing the `/var/run/docker.sock` from the host, to execute docker commands.
