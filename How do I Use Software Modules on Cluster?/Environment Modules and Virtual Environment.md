# Environment Modules

Environment Modules (or modules) are used to manage the user environment for the installed packages. This makes it simple to use different packages or switch between versions of the same package without conflicts.
The commands for environment modules:
- `module avail` : List of application software that is installed on the HPC 
- `module load packageName`: Loads the specified package with specified version 
- `module list`: List the uploaded application softwares 
- `module unload packageName`: Unloads the specified package with specified version 
- `module purge`: Unload all packages from user environment.

⚠️⚠️⚠️ Do not use wget or any other ways to install software. If you do you can have problems about job submitting and it will slow down your remote computer.<br>

⚠️⚠️⚠️ You can load necessary module through job scripts or terminal. But, wise thing to do is creating a job script to load modules such as gcc, cuda and adding to .bashrc file or run it every time. You can create different job scripts which includes necessary modules for specific projects.
If you want any other software installed, or a different version, send a request email ​hpc-support@ku.edu.tr.​ Please include a detailed information about the software like web page, version, license etc. Note that if the software requires a licence, the users of the software will need to purchase the licence.

# How to create a Virtual Environment?

List modules and choose an anaconda version from list.
```
module avail
module load anaconda/x.x.x (version you choose)
```

Now, you will have conda command running since it was added into your PATH.
```
conda create -n env_name python=x.x.x anaconda
```

You will have conda virtual environment installed under your home folder (/kuacc/users/username/.conda/)

You can activate/deactivate virtual env by:
```
source activate env_name
```

You can install any **software** under your evironment by “pip install” or “conda install” commands.
```
pip install package_name
```

In order to deactivate virtual environment
```
source deactivate
```

You need to add
```
module load anaconda/x.x.x
source activate env_name
```

Run your code.
```
source deactivate env_name
```
into your job script.

If you want to remove the virtual environment:
```
conda remove -n env_name -all -y
```

 
⚠️⚠️⚠️ If you get an error like this while pip install in virtual environment:<br>

`PermissionError: [Errno 13] Permission denied: '/kuacc/apps/anaconda/3.6….`<br>

This is because the package you want to install tries to write under /kuacc/apps, which you do not have permission to access. Another reason is trying to remove the default packages that create env.<br>

To fix the problem, you can force the home folder to be used by using the --user statement.<br>
`pip install -r requirements.txt --user`
 
