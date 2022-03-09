




____ This tutorial/code only works on Linux system ___

-Step 0, you may be interested in getting the controls / monitoring app to view the usage of VRAM and RAM
-as well s having a fan control on your gpu

AMD
https://github.com/marazmista/radeon-profile

NVIDIA (GreenWithEnvy)

https://www.flathub.org/apps/details/com.leinardi.gwe
https://flatpak.org/setup/Ubuntu


flatpak install flathub com.leinardi.gwe

flatpak run com.leinardi.gwe



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

Step 0.2

-the instruction here are mostly based on this tutorial made by Blake, it would be a good idea
-to have a look at it and what is happening, Im basically using 95% of code from here and
-just simplified it for Anons

"Fine-tuning GPT Neo 2.7B and 1.3B"
https://www.youtube.com/watch?v=Igr1tP8WaRc



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

HOW TO START

-get Ubuntu (or other linux distro, dunno much about those to give a in-depth recommendation)

(optionally get the 'GreenWithEnvy' to monitor your nvidia gpu card usage and 'GNOME System Monitor' for the ram)

(watch tutorial from Step 0.2) https://www.youtube.com/watch?v=Igr1tP8WaRc



-install anaconda

https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html

// remember that commands 'ls' (show files inside this folder) and 'cd' (return/go to the folder) are your friend



//following bellow are terminal command needed to install all the necessary elements for jupyter, deepspeed and nvidia requirements



bash

//list all the environments you have created in anaconda, when starting you will only see the 'base' standard one

conda info --envs

//create and activate environment just for training gpt with deepspeed, press 'y' to confirmed installation modules


conda create -n PPPds python=3.7

//activate new environment, in terminal you should see a change of (base) to (PPPds)

//once you installed everything and successfully run the test you can than just run
//below command, "cd to folder", "jupyter notebook" and the Step 3 for your custom training

conda activate PPPds

conda install jupyter

//turn the environment into usable kernel for the training file

python -m ipykernel install --user --name=PPPds

//make sure the zip 'PPPdeepspeed' folder (with training file and single txt 'readme' file) is unzip to desktop, than run

cd Desktop/PPPdeepspeed

ls

//before opening and running the training file we will need to install few more requirements bits for smooth operation

sudo apt-get install git

conda install -c conda-forge nvcc_linux-64

conda install -c conda-forge cudatoolkit-dev=11.1

sudo apt-get install -y libaio-dev

pip install triton==1.0.0


//run this to open the jupyer and use the browser as the UI. if nothing happens, press Control+C in termial, open rbrowser and run below command again


jupyter notebook


// IMPORTANT, once opening the training file, go to 'Kernel' -> 'Change Kernel' dropdoown menu and select 'PPPds'
//Click on 'not trusted' to allowed the code to be 'Trusted'
//Restart the kernel with the icon on the top




//open the preparation training file, for the first time you will need to run all the cells in parts from top to bottom, "pytorch and cuda", "deepspeed bulding", "finetune training"
//however if this is your second time running this script you should have already installed all of the above elements for you 'gptneo_finetuned' envitiments so 
//you will need to just edit and run the last "finetune training" cell

//All training datasets will need to be placed in the "finetune-gpt2xl" folder (it will be created after you run the test finetune code)


