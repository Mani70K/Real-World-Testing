# Real-World Testing (RWT Reporting Project)

# Technology Used
  Frontend:- Jenkins Ops Tool
  Backend:-  .Net 8, Advanced .Net(Task Parallel Library & Asynchronous Programming)
  Cloud Technology:- AWS ECS, AWS Cloudwatch Metrics, AWS RDS(AWS Aurora), AWS S3 Bucket
  Database:- PostgreSQL
  
# Introduction
Real World Testing Project was a Regulatory requirement project. In This Project, We have used .Net 8 As Backend Technology and Jenkins Ops Tools for Frontend development.We as dev platform(Team) developers, we have implemented the project from scratch and also created a new reportsitory for this project. We have used AWS ECS Task to launch the application or we have deployed our application to the AWS ECS(Elastic Container Service).In the project, We have used TPL(Task Parallel Library) and Asynchronous programming,so that we can optimized our application performance through parallel programming.The TPL allows us to create a dataflow blocks and this dataflow block is used to pass the information from one block to another block and also we can create a pipeline using TPL so that our ECS Task will execute each dataflow bl sequentially.After Successful execution of all the blocks, our ECS task will generate a report(.csv file) in the AWS S3 Bucket. 

# Methodology
1. 
