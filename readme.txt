You Need to run this in python 3.11.6, not the most recent version.
Use a powershell terminal, and get the older version with 
> Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
Check that it works by running "pyenv --version" in terminal, then run
> pyenv install 3.11.6
Then locate the folder "finalproject" through the terminal, and run
> pyenv local
(this is just to check if pyenv already has a local version, and can be skipped)
> pyenv local 3.11.6


For you're first time, you'll have use pip install XXX to install the various imports here


For running the model, run this, and switch your network to whatever .pkl file you have that was trained.
There is a pretrained file named ffhq.pkl that you can use if you do not have a pre-trained .pkl file, and it will just need to be copied
> python generate.py --outdir=out --trunc=1 --seeds=1-5 --network=YOURFILE.pkl
If you want to test it out, move ffhq.pkl/YOURFILE.pkl to the same space as the folder "finalproject", and change the command to match. 
Your images will be in finalproject/stylegan2-ada-pytorch/out/seedXXXX.png
You can make as many as you want, using any non-negative number as a seed, and using commas for individual seeds, and a dash for the range


To train your own model (You will Need a GPU to do this)
https://www.xnview.com/en/xnview/#features - get this program, and then navigate to a folder of the images you wish to make ML versions of 
Select your pictures, and press ctrl+u, and then change them to be the dimensions and the same file format. Make sure to save these to a NEW FOLDER, so your old images don't get replaced.
For training the model on your own images, change all the images to the same file type and the same height and width, and then zip the folder, then change -data to the location of the zip file.
> python train.py --outdir=./training-runs --data=C:\Users\herop\OneDrive\Documents\!College\!ComputerVision\projectfinal\YOURIMAGES.zip --gpus=1 --cfg=auto


sources used:
https://github.com/NVlabs/stylegan2
https://github.com/NVlabs/ffhq-dataset
