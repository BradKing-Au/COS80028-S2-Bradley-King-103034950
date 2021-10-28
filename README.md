# COS80028-S2-Bradley-King-103034950

#Bradley King COS80028 Transportation Forecast Readme and User Documention

This repository may be accessed locally by opening a Command Prompt with git installed,
navigating to the desired directory to store the project and entering
> git clone  https://github.com/BradKing-Au/COS80028-S2-Bradley-King-103034950.git

You will be prompted to enter you GitHub username and access token to prove your identity
and the repository will be downloaded to your local machine.

This project cannot be run without the formatted_raw_data folder. Due to a Non-disclosure agreement, data may not be stored in online repositories.
Should you have access to the formatted_raw_data folder, please place it in the project directory as shown below.

##Initial directory setup

Parent Directory

--|formatted_raw_data
----|EB14010.csv
----|EB14032.csv
----|EB14045.csv
----|EB14061.csv
----|WB14003.csv
----|WB14031.csv
----|WB14051.csv
----|wb14063.csv
--|Data LoadingEB.ipynb
--|Data LoadingWB.ipynb
--|eb_models.ipynb
--|wb_models_and_hyperparameter_tuning.ipynb
--|gifcreation.ipynb
--|readme.RD
--|anvil_web_code.txt

Directory after importing formatted_raw_data from external source

This documentation assumes that most code will be ran using Anaconda Navigator and Jupyter Notebook.  
eb_models.ipynb and wb_models_and_hyperparameter_tuning.ipynb benefit from GPU acceleration during model training.
It is assumed that these files will be ran on Google Colab for the benefit of this hardware acceleration, and the virtual environment
provided in this documentation does not natively install tensorflow and other libraries required for these notebook files.



##Virtual Environment creation

Open anaconda prompt and naviagte to project directory
Create a virutal environment using
> conda create -n <environment_name>
press y to proceed

The environment may activated by typing
> conda activate <environment_name>

Data LoadingEB.ipynb and Data LoadingWB.ipynb pip install the necessary libraries to function.

##Running Dataloading Files Locally

To run jupyter notebook, start Anaconda Navigator
The newly created virtual environment may be activated within Anaconda Navigator by selecting it from the dropdown menu at the top of the screen.
Install and then launch Jupyter Notebooks.
Jupyter Notebooks will launch in your default browser. Within Jupyter Notebook, navigate to the project directory,
open the Data LoadingEb.ipynb or Data LoadingWBipynb and select Cell>Run All from the menubar at the top of the screen.

These dataloading files import the CSVs for each direction, concatenate them into a single dataframe, and remove missing values using interpolate and removing rows by index and Date.
These cleaned dataframes and saved as csv files in the clean_data directory.
After running the dataloading files, the project directory will be as displayed below.


Directory after running Data LoadingEB.ipynb and Data LoadingWB.ipynb:

Parent Directory

--|formatted_raw_data
----|EB14010.csv
----|EB14032.csv
----|EB14045.csv
----|EB14061.csv
----|WB14003.csv
----|WB14031.csv
----|WB14051.csv
----|wb14063.csv
--|clean_data
----|ebdataset.csv
----|wbdataset.csv
--|Data LoadingEB.ipynb
--|Data LoadingWB.ipynb
--|eb_models.ipynb
--|wb_models_and_hyperparameter_tuning.ipynb
--|gifcreation.ipynb
--|readme.RD
--|anvil_web_code.txt

##Running model develpment notebook files remotely on Google Colaboratory

To run wb_models_and_hyperparameter_tuning.ipynb or eb_models.ipynb on Google Colaboratory, open a web browser and navigate to https://colab.research.google.com/

Google Colabatory will open a prompy asking which notebooks files to run. Select Upload from the menubar, navigate to the project directory and select the file to be ran.
Select Runtime from the Menu bar, then 'Change Runtime Type'
Ensure hardware acceleration is set to GPU and save.

Run Cells 1 and 2 to import libraries and pip install StellarGraph, which is the only required library that is not natively on Google Colabs virtual environment.
Run Cell 3, which will prompt you to upload a file. Navigate the the project_directory/clean_data/ and select the relevant dataset for the notebook file being ran, and select okay.
The rest of the notebook may be ran by selecting cell 4, and selecting Runtime>Run After from the menubar.
The notebook files write and populate predictions, truths, model_performances, EBmodels and WBmodels files. Google Colab will zip and download outputs to the local computer after runtime has been completed.
Please unzip the notebook files and assemble the new folders within the project directory as shown below.

If running these files on a local virtual environment that supports GPU acceleration, they will attempt to pip install StellarGraph to the environment.
If running these files locally, please comment out cell 3, and the final cell which are for importing and exporting files from google colabs working directory.


Directory after running wb_models_and_hyperparameter_tuning.ipynb and eb_models.ipynb

--|formatted_raw_data
----|EB14010.csv
----|EB14032.csv
----|EB14045.csv
----|EB14061.csv
----|WB14003.csv
----|WB14031.csv
----|WB14051.csv
----|wb14063.csv
--|clean_data
----|ebdataset.csv
----|wbdataset.csv
--|predictions
----|eb5minpred.csv
----|eb10minpred.csv
----|eb15minpred.csv
----|eb30minpred.csv
----|eb45minpred.csv
----|eb60minpred.csv
----|wb5minpred.csv
----|wb10minpred.csv
----|wb15minpred.csv
----|wb30minpred.csv
----|wb45minpred.csv
----|wb60minpred.csv
--|truths
----|eb5.csv
----|eb10.csv
----|eb15.csv
----|eb30.csv
----|eb45.csv
----|eb60.csv
----|wb5.csv
----|wb10.csv
----|wb15.csv
----|wb30.csv
----|wb45.csv
----|wb60.csv
--|model_performances
----|ebcorrmatrix.csv
----|eb_test_losses_time
----|eb_train_losses_time
----|eb_val_losses_time
----|wbcorrmatrix.csv
----|wb_test_losses_time
----|wb_train_losses_time
----|wb_val_losses_time
--|EBmodels
----|eb5
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb10
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb15
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb30
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb45
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb60
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
--|WBmodels
----|wb5
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb10
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb15
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb30
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb45
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb60
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
--|Data LoadingEB.ipynb
--|Data LoadingWB.ipynb
--|eb_models.ipynb
--|wb_models_and_hyperparameter_tuning.ipynb
--|gifcreation.ipynb
--|readme.RD
--|anvil_web_code.txt

##Creating Dashboard Visualisations Locally

After populating the predictions and truths folders using the eb_models.ipynb and wb_models_and_hyperparameter_tuning.ipynb,
sample visualisations to be deployed to the dashboard may be generated.

Open Anaconda Navigator, select the virutal environment created above and launch Jupyter notebooks.
Navigate to the project directory within Jupyter notebooks and run gifcreation.ipynb.
This populates the visualisations folders.


Directory After running gifcreation.ipynb

--|formatted_raw_data
----|EB14010.csv
----|EB14032.csv
----|EB14045.csv
----|EB14061.csv
----|WB14003.csv
----|WB14031.csv
----|WB14051.csv
----|wb14063.csv
--|clean_data
----|ebdataset.csv
----|wbdataset.csv
--|predictions
----|eb5minpred.csv
----|eb10minpred.csv
----|eb15minpred.csv
----|eb30minpred.csv
----|eb45minpred.csv
----|eb60minpred.csv
----|wb5minpred.csv
----|wb10minpred.csv
----|wb15minpred.csv
----|wb30minpred.csv
----|wb45minpred.csv
----|wb60minpred.csv
--|truths
----|eb5.csv
----|eb10.csv
----|eb15.csv
----|eb30.csv
----|eb45.csv
----|eb60.csv
----|wb5.csv
----|wb10.csv
----|wb15.csv
----|wb30.csv
----|wb45.csv
----|wb60.csv
--|model_performances
----|ebcorrmatrix.csv
----|eb_test_losses_time
----|eb_train_losses_time
----|eb_val_losses_time
----|wbcorrmatrix.csv
----|wb_test_losses_time
----|wb_train_losses_time
----|wb_val_losses_time
--|EBmodels
----|eb5
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb10
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb15
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb30
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb45
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|eb60
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
--|WBmodels
----|wb5
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb10
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb15
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb30
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb45
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
----|wb60
------|assets
------|variables
------|keras_metadata.pb
------|saved_model.pb
--visualisations|
----eb5animation.gif
----eb10animation.gif
----eb15animation.gif
----eb30animation.gif
----eb45animation.gif
----eb60animation.gif
----wb5animation.gif
----wb10animation.gif
----wb15animation.gif
----wb30animation.gif
----wb45animation.gif
----wb60animation.gif
--|Data LoadingEB.ipynb
--|Data LoadingWB.ipynb
--|eb_models.ipynb
--|wb_models_and_hyperparameter_tuning.ipynb
--|gifcreation.ipynb
--|readme.RD
--|anvil_web_code.txt

After running gifcreation.ipynb the contents of the visualisations folder was hosted on gifyu.
Anvil.works was used to create a dashboard to host these visualisations.
Anvil.works front end devlopment is written in python and can be seen in the anvil_web_code.txt file.
Dropdown_1 and plotspace are a dropdown menu bar and img window placed into form 1 using Anvil's GUI webapp designer.
The resulting webapp is hosted at https://round-sugary-mate.anvil.app/
