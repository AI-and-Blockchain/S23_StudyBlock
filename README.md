# S23_StudyBlock
# Project Description 
To create a platform that allows cancer researchers and patients to be matched to clinical trials and research studies according to their needs. The project will use AI to provide matches for researchers and patients. The project will require blockchain in order for patients and/or researchers to be able to contact the point of contact of the clinical trials or research studies where there can also be a safe medium of private data exchange if need be.

### Motivation ###
Improve patient and researcher access to clinical trials and research studies which in turn benefits the trials and studies as well.

### Final Goal ###
To allow patients and researchers to be matched with clinical trials that match their needs and to allow researchers to negotiate for clinical research data on the blockchain.


### User Stories ###
As a breast cancer patient, I want to be able to further look into the effects and results of a clinical trial to find the one that best suits my needs. 

As a researcher, I want to find clinical trial data related to my current study to help support my current research.

### StudyBlock User Work Flow ###
```mermaid
sequenceDiagram;
    Participant A as Research Owner
    Participant B as Researcher
    Participant C as Patient
    Note over A: Advertises Clinical Trial <br> to BlockChain
    Note over A: Stores trial description in shared database
    Note over B, C: Uses NLP Algorithm <br> to search for <br> relevant studies
    Note over B,C: Researcher/Patient <br> finds a matching study
    B -> A: Researcher reaches <br> out to research owner, <br> research owner can chose <br> to then share off-chain
    C -> A: Patient reaches out <br> to research owner
```

### StudyBlock Architecture ###
```mermaid
sequenceDiagram;
    Participant B as BlockChain layer
    Participant C as User
    Participant A as NLP powered search engine
    C -> A: Triggers search feature
    A -> C: Returns list of relevant studies
    C -> B: User uses atomic contract <br> to privately message research owner
    C -> B: Research owner uses atomic <br> contract to privately messager <br> participant or researcher 
```

# Instructions

## Installation ##

### Getting Started ###

Clone this github repo:

``` 
git clone https://github.com/AI-and-Blockchain/S23_StudyBlock.git
```

Download our test data as a csv:

```
https://docs.google.com/spreadsheets/d/1nBnqNMZMN4zYPI4_bdbiWCXIne6HrEFAvWLzhznfYqU/edit?usp=share_link
```

This data comes from https://clinicaltrials.gov

### Dependencies ###

After cloning this repo, install requirements from requirements.txt by running the following command:

``` 
pip install -r requirements.txt
```

Following this, install the NLP model from this link:
```
https://allenai.github.io/scispacy/
```

Download the url for "en_core_sci_sm", then run the following commands:

```
pip install scispacy
pip install <Model URL>
```

Our project is run on algorand and our NLP model uses SpaCy and sciSpaCy. 

We use the package algosdk to develop in algorand using python, to find out more about this visit the following link:

```
https://py-algorand-sdk.readthedocs.io/en/latest/
```


## Usage ##

This project is *currently* run on a command line interface. To do this start by running the file 'cmdgui.py'. Then follow the command line prompts to run the project.

#### Example Inputs and Expected Results ####
Researcher [R] or Patient [P]?
p
Please enter any search terms: 
atypia
Here are a list of current trials in that area:
1 Vitamin D and Breast Cancer Biomarkers in Female Patients
2 test trial
3 4D Image-Guided Partial Breast Radiation in Stage 0 and l Breast Cancer
Which trial would you like to access? (number)
3
Accessing 4D Image-Guided Partial Breast Radiation in Stage 0 and l Breast Cancer
Would you like to contact the researcher?
y
Enter your address: 
2W4PBQN3ZTAG54D3MM2CJDLN4WTDTQJVV2W4AHO7SHYOSDIDWV6HM2B3KM
Enter private key: 
L+ds9q28iYcsgeu/5BOX8ZSHd4KUup2q4/SutqLeCDPVuPDBu8zAbvB7YzQkjW3lpjnBNa6twB3fkfDpDQO1fA==
Enter receiver address: 
BU5IN3BOIYVWD3TW2XQFOQJ3EGFFYCMHN24JBNMR5IU2LWST74TPZAQYBI
Enter message: 
I would like to participate
Transaction sent with ID OXA5SLMFLV3IUQVHVYUFS6UOVV2CRS4SQ2ARXFXMAYQZ7NRSEZLA
Waiting for confirmation
Transaction confirmed in round 29127673


## Project Structure ##
```
- root
        - Messaging                                 (Code for Blockchain messaging and encryption)
                ClinicalTrial.py
                ClinicalTrialMessaging.py  
        - Models                                    (Code to create our model and enable searches)
                nlp.py
                test-model.py
                trialdata.csv                       (Trial data)    
        atomicContract.py                           (Atomic Contract code)
        oracle.py                                   (Oracle code)
        cmdgui.py                                   (Command Line interface)
        page.html                                   (Web interface)

```

