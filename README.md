# Pester Linux Runner
Provides an image to run Pester tests in a Linux environment. It also includes other utilities like `curl` and `docker`.

## Usage

It will run all the tests found in the folder `/test`. This can be a volume or a folder that is copied when creating another image.

`Docker` is also available, it can be used to mount a volume sharing the `/var/run/docker.sock` from the host, to execute docker commands.

Ex: `docker run -v /var/run/docker.sock:/var/run/docker.sock -v <FOLDER_IN_HOSTMACHINE_WITH_TESTS>:/test`
