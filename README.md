# Dockerfile Bug: Missing Dependencies in Python Test Environment

This repository demonstrates a common error in Dockerfiles: failing to install project dependencies before running tests. The original `Dockerfile` attempts to run unit tests using `unittest` but doesn't specify the necessary packages, leading to test execution failure inside the container. The solution is demonstrated in `Dockerfile.fixed`. 

## Bug

The original `Dockerfile` includes `python3` and `pip`, but omits installing project dependencies.  This leads to a runtime error when `unittest` attempts to import project modules which have external dependencies that are not installed.

## Solution

The `Dockerfile.fixed` addresses the issue by introducing a `requirements.txt` file specifying the needed packages and using `pip install -r requirements.txt` to install them before executing the tests. This ensures the testing environment is correctly set up.