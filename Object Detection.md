# Sign language detection using Raspberry PI and Camera

<br/>

Since we have an assembled RC smart car with its OS installed, we could initialize our commands in the terminal of its operation system after plugging the power supply and connecting the Raspberry PI to a monitor via HDMI. <br/>
The first thing we needed to do is to update all the installed packages:
```
sudo apt-get update
```

<br/>

Then, installing pip3 followed:
```
sudo apt install python3-pip
```
Also, we needed to upgrade it to the latest version:
```
sudo -H pip3 install --upgrade pip
```

<br/>

After that, we created our virtual environment using the following command:
```
sudo -H pip3 install virtualenv
```
After installing our virtual environment, we created a directory called 'jupyter' for virtual environment and navigated into it:
```
mkdir jupyter
```
```
cd jupyter
```
The next thing we did is that we created a python virtual environment with the name of 'environment' inside of this directory:
```
virtualenv environment
```
In order to activate this virtual environment, we used the following command:
```
source environment/bin/activate
```

<br/>

Then, we cloned a template for our real time object detection project from a github repository:
```
git clone https://github.com/nicknochnack/RealTimeObjectDetection
```
...which downloaded the template and cloned it into our virtual environment.

<br/>

The next step is to use Jupyter Notebook for running commands. To do that, first, we installed jupyter in our virtual environment:
```
pip install jupyter
```
Now, we can open Jupyter Notebook with the following command:
```
jupyter notebook
```

<br/>

So, the Chromium browser opened a new tab automatically for Jupyter Notebook. Then we created a new file with the name of ```Body_language_signs.ipynb``` inside of the RealTimeObjectDetection template that we have downloaded and ran the commands as in that file.

<br/>

The following process can be seen by the demo video:
[Demo video](https://youtu.be/W1h08Tyr6t8)
