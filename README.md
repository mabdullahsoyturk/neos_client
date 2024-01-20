# NEOS Client

This is a Neos Client for [NEOS Server: XML-RPC api](https://neos-server.org/neos/xml-rpc.html). While [the official client](https://github.com/NEOS-Server/PythonClient) only provides a queue or submit job call, this client supports the following methods:

* `is_alive()`: Equivalent to sending a ping to the server and checking the result.
* `get_job_status(job_number, job_password)`: Equivalent to getJobStatus(jobNumber, password) in NEOS Server RPC.
* `get_completion_code(job_number, job_password)`: Equivalent to getCompletionCode(jobNumber, password) in NEOS Server RPC.
* `get_job_info(job_number, job_password)`: Equivalent to getJobInfo(jobNumber, password) in NEOS Server RPC.
* `kill_job(job_number, job_password, message)`: Equivalent to killJob(jobNumber, password, killmsg="") in NEOS Server RPC.
* `get_final_results(job_number, job_password, is_blocking)`: Equivalent to getFinalResults(jobNumber, password) if it's blocking. If it's not blocking, it Equivalent to getFinalResultsNonBlocking(jobNumber, password).
* `email_job_results(job_number, job_password)`: Equivalent to emailJobResults(jobNumber, password) in NEOS Server RPC.
* `get_intermediate_results(job_number, job_password, offset, is_blocking)`: Equivalent to getIntermediateResults(jobNumber, password, offset) if it's blocking. If it's not blocking, it Equivalent to getIntermediateResultsNonBlocking(jobNumber, password).
* `download_output(job_number, job_password, working_directory)`: Downloads the results and extracts the files to the given working directory. It Equivalent to getOutputFile(job_number, job_password) in NEOS Server RPC and extracting it to the working directory.
* `print_queue()`: Prints the current queue on the server if the server is alive.
* `submit_job(xml_path, is_blocking, working_directory)`: If the username and password is given, it is equivalent to authenticatedSubmitJob(xmlstring, user, password). If the username or password is not given, it is equivalent to submitJob(xml_string). If it's blocking, it waits until all the results are received. If it's non-blocking, it immediately returns after submitting the job.

## Installation

```
pip install neos_client
```

or 

```
git clone git@github.com:mabdullahsoyturk/neos_client.git
cd neos_client
pip install .
```

## Usage

```Python
from neos_client import NeosClient

client = NeosClient(email=<your_email_address>)
client.submit_job(xml_path=<path_to_your_xml_file>)
```
