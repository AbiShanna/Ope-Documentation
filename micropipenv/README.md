# &nbsp; Adding new python library

The s2i images uses [micropipenv](https://github.com/thoth-station/micropipenv) a pip wrapper tool to install the python libraries.

### To generate requirements.txt from scratch:
<br/>In your local workstation that has docker installed, 
1. Docker run into the base s2i image:
<br/> &nbsp; &nbsp;&nbsp; *docker run -it quay.io/thoth-station/s2i-minimal-py38-notebook:v0.3.0 /bin/bash*
2. In a empty folder, place your packages.txt file with list of libraries to install. 
3. Run *'pipenv shell'* to launch a new shell. A new Pipfile will be created. Install packages just like pip as <br/> &nbsp; &nbsp; &nbsp;*pipenv install -r packages,txt* <br/>This will automatically update the pipfile and generate lock.

4. Generate requirements.txt, requirements.in like :
<br/> &nbsp; &nbsp;&nbsp; *micropipenv requirements --no-dev > requirements.txt*
<br/> &nbsp; &nbsp;&nbsp; *micropipenv requirements --no-dev --only-direct > requirements.in*

5. Replace this requirements.txt in the s2i container repo.
<br/>

### To add a new package to existing requirements.txt as:

1. Copy all the files in the folder into your base image/container in a separate folder.
2. Run *pipenv shell* to launch a new shell. 'pipenv' is available by default in s2i images (install otherwise).

3. In the folder with the copied files, install the required packages as

     &nbsp; &nbsp; &nbsp; &nbsp; *pipenv install <library_name>*

4. Generate requirements.txt, requirements.in like :
<br/> &nbsp; &nbsp;&nbsp; *micropipenv requirements --no-dev > requirements.txt*
<br/> &nbsp; &nbsp;&nbsp; *micropipenv requirements --no-dev --only-direct > requirements.in*

5. Replace this requirements.txt in the s2i container repo.
<br/>
<br/> For more information and examples, see this [blog post](https://dev.to/fridex/micropipenv-the-one-installation-tool-that-covers-pipenv-poetry-and-pip-tools-3ee7).
