# Python streamsx.inet package

This exposes SPL operators in the `com.ibm.streamsx.inet` toolkit as Python methods.

Package is organized using standard packaging to upload to PyPi.

The package is uploaded to PyPi in the standard way:
```
cd package
python setup.py sdist bdist_wheel upload -r pypi
```
Note: This is done using the `ibmstreams` account at pypi.org and requires `.pypirc` file containing the credentials in your home directory.

Package details: https://pypi.python.org/pypi/streamsx.inet

Documentation is using Sphinx and can be built locally using:
```
cd package/docs
make html
```

or

    ant doc

and viewed using
```
firefox package/docs/build/html/index.html
```

The documentation is also setup at `readthedocs.io`.

Documentation links:
* http://streamsxinet.readthedocs.io/

## Version update

To change the version information of the Python package, edit following files:

- ./package/docs/source/conf.py
- ./package/streamsx/inet/\_\_init\_\_.py

When the development status changes, edit the *classifiers* in

- ./package/setup.py

When the documented sample must be changed, change it here:

- ./package/streamsx/inet/\_\_init\_\_.py
- ./package/DESC.txt

## Test

### Streaming Analytics service in IBM Cloud

Package can be tested with TopologyTester using a local toolkit and launch the job in [Streaming Analytics](https://www.ibm.com/cloud/streaming-analytics) service.

Ensure that inet toolkit location is part of STREAMS_SPLPATH:

    export STREAMS_SPLPATH=$STREAMS_INSTALL/toolkits/com.ibm.streamsx.inet

Run the test with:

    ant test-sas

or

```
cd package
python3 -u -m unittest streamsx.inet.tests.test_inet.TestHTTPStreamingAnalytics
```

#### Remote build

For using the toolkit from the build service (**force_remote_build**) run the test with:

Run the test with:

    ant test-sas-remote

or

```
cd package
python3 -u -m unittest streamsx.inet.tests.test_inet.TestHTTPStreamingAnalyticsRemote
```


### Local Streams instance

Package can be tested with TopologyTester using a local and running Streams domain.
Make shure that the streams environment is set, the domain and instance is running and the environment variables:
STREAMS_USERNAME
STREAMS_PASSWORD
are setup.

Ensure that inet toolkit location is part of STREAMS_SPLPATH:

    export STREAMS_SPLPATH=$STREAMS_INSTALL/toolkits/com.ibm.streamsx.inet


Run the test with:

    ant test

or

```
cd package
python3 -u -m unittest streamsx.inet.tests.test_inet.TestHTTPDistributed
```
