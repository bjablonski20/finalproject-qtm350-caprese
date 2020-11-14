# Assessing Accuracy of Amazon Transcribe at Increasing Speech Speeds: Demo
This demo solution and Github repo demonstrates how to test the accuracy of Amazon Transcribe at increasing levels of speech speed. It consists of both the data used in this solution as well as the notebook and code to recreate the solution 

## Data
For this example, 8 different texts are read. Each text is read and recorded 10 different times at 5 different speeds: 75 words per minute, 125 words per minute, 175 words per minute, 225 words per minute, and 275 words per minute. 

All audio files and text files are saved under the "Input Data" folder. Inside of this folder, these files are segmented by document number. 
- Doc 1: This document is the opening lines to *The Tale of Two Cities*
- Doc 2: This document is an excerpt from a [research paper](https://arxiv.org/pdf/1807.02221.pdf) titled "THE DATA SCIENCE OF HOLLYWOOD: USING EMOTIONAL ARCS OF MOVIES TO DRIVE BUSINESS MODEL INNOVATION IN ENTERTAINMENT INDUSTRIES".
- Doc 3: This document is an excerpt from an [article](https://fivethirtyeight.com/features/final-2020-house-forecast/) from 538 titled "Final Forecast: Democrats Are Clear Favorites To Maintain Control Of The House".
- Doc 4: This document is the opening lines from *The Iliad*.
- Doc 5: This document is three [tweets](https://twitter.com/realDonaldTrump) from Donald Trump.
- Doc 6: This document is an excerpt from an [article](https://fivethirtyeight.com/features/final-2020-presidential-election-forecast/) from 538 titled "Biden’s Favored In Our Final Presidential Forecast, But It’s A Fine Line Between A Landslide And A Nail-Biter".
- Doc 7: This document is an excerpt from a [research paper](https://www.researchgate.net/publication/339500868_Applications_of_Topic_Models) titled "Applications of Topic Models".
- Doc 8: This document is three [tweets](https://twitter.com/JoeBiden?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor) from Joe Biden. 

## Demo Solution and Recreation 
This section will demonstrate how to recreate the solution shown in the notebooks. 
1. Clone this Github Repo: This can be done by running the following code in a code cell in your Jupyter Notebook in a Sagemaker instance. 

`!git clone https://github.com/bjablonski20/finalproject-qtm350-caprese.git`

2. Provide your Sagemaker Execution IAM Role with AmazonTranscribeFullAccess Role: This can be done in one of two ways.
    - Go to the IAM role that you wish to alter. Click attach policy, and search for AmazonTranscribeFullAccess. Click on the policy and attach it. 
    - Alternatively, you can attach the following JSON policy to your Sagemaker Execution Role. This JSON is also saved in the Github Repo under the IAMPolicies folder. 
    
`
{

    "Version": "2012-10-17",
    
    "Statement": [
    
        {
        
            "Effect": "Allow",
            
            "Action": [
            
                "transcribe:*"
                
            ],
            
            "Resource": "*"
            
        },
        
        {
        
            "Effect": "Allow",
            
            "Action": [
            
                "s3:GetObject"
                
            ],
            
            "Resource": [
            
                "arn:aws:s3:::*transcribe*"
                
            ]
            
        }
        
    ]
    
}
`

3. Run the code cells in the QTM350_FinalProject_BlogPost.ipynb notebook. If you do not want to create your own transcribe jobs, you can skip the third code cell in the notebook. If you do want to create your own transcribe jobs, follow the instructions below. 

- Create an S3 Bucket. Copy its name.

- Replace the OutputBucketName in third code cell. This will create and save transcribe jobs to your S3 Bucket. 



