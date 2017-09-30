# Locations  API Integration Tests

This directory contains files that run integration tests against the locations API. To run the tests, use Python. These libraries are required to run the integration tests:

* [json](https://docs.python.org/2/library/json.html)
* [requests](http://docs.python-requests.org/en/master/)
* [unittest](https://docs.python.org/2/library/unittest.html)
* [ssl](https://pypi.python.org/pypi/ssl/)
* [urllib2](https://docs.python.org/2/library/urllib2.html)
* [pyOpenSSL](https://pypi.python.org/pypi/pyOpenSSL)

Use this command to run the tests:

	python integrationtests.py -i /path/to/configuration.json

Any unittest command line arguments should be used before the -i argument. For example, this command will run the tests in verbose mode:

	python integrationtests.py -v -i /path/to/configuration.json

Python Version: 2.7.10

### Docker

This directory contains files that run integration tests against the Locations Frontend API.

First, create a configuration.json file from configuration_example.json.

Next, use these commands to build and run the container. All you need installed is Docker.

```shell
$ docker build -t locations-tests .
# Run the integration tests in Unix
$ docker run -v "$PWD"/configuration.json:/usr/src/app/configuration.json:ro -v /path/to/cert.pem:/tmp/api.pem:ro locations-tests
# Run the integration tests in Windows
$ docker run -v c:\path\to\configuration.json:/c:\usr\src\app\configuration.json:ro -v /path/to/cert.pem:/tmp/api.pem:ro locations-tests
```

## Configuration.json Notes

If you are using Docker for Mac (as of 17.06) the localhost name will be https://docker.for.mac.localhost:8080/api/v1/locations