# LTI-Heartbeatlog-s
In this project i have create 4 pipeline using Azure Data Factory.


Scenarios :
Data is generated in real-time through an application which we need to store in an azure Files Share . The Data is compressed from the application size in the .gzip file so that it becomes easy to Send over the network data size is unpredictable it's in GB's as estimated.

Problem :
The client wants that data in. JSON Format to build a recommendation ML Model
 As we were using a simple Move pipeline Created using Azure Data Factory it failed to move data because of the below reasons.
The size of data is not consistent concerning the time
if some log file is corrupted Due to network failure Data factory is not able to extract these Files Due to which pipeline failed.

Solution :
1 I have Built a  pipeline with will move data in batches of 15 min each.
2 we have used a custom activity in our pipr=eline with will run a python code to detected those corrupted .gz Files and move that file in error Folder

Conclusion :
In total, we have Created 4 Pipeline 
1 to move data in the batch of 15 min each for every 1hr.
2 exception pipelines will detect the error files and move them.
3 this pipeline is the same as pipeline 1st  but the only difference with the Time Configuration is it will run in every 3hr with 15 min batch time
4 This pipeline is the same as 1st pipeline but I have created it to run with custom date-time data parameterized.

