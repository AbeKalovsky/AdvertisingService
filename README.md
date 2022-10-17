#  Unit 7 Project: ATA Advertising Service

## Preliminaries: The More Things Change

### Ambiguity, Complexity, and Scope

Ambiguity will be increasing from previous projects. Tasks instructions will contain fewer details, as we expect you to 
reference documentation and deep dive into the code yourself to understand how things work. Even if there isn't a 
specific task for it, you're of course welcome to create any diagrams or other notes as a reference for yourself or 
others!

There will be some increasing complexity as we work with ExecutorServices for the first time.

You'll have your fellow participants in the same situation as you, so remember to collaborate: rely on each other for 
assistance, and share your own knowledge.

## Unit 7 Project Progress and Tracking

### Doneness checklist

You're done with the project when: 

* You have successfully passed all tests in CodeGrade

### cloudformation commands

You'll want to run the following commands to setup your DynamoDB tables for this project (note that you will need to wait for the first command's stack to finish building before running the next commands):

```
aws cloudformation create-stack --region us-west-2 --stack-name advertisingservice-createtables --template-body file://configurations/cloudFormation/ddb_tables.template.yml --capabilities CAPABILITY_IAM
aws dynamodb batch-write-item --request-items file://configurations/cloudFormation/content_table.json
aws dynamodb batch-write-item --request-items file://configurations/cloudFormation/targeting_group_table.json
aws dynamodb batch-write-item --request-items file://configurations/cloudFormation/targeting_group_table2.json
```

## The Problem: ATA Advertising

ATA's AdvertisingService serves advertisements for ATA. These advertisements show up on the retail website and use 
targeting to present different ATA advertisements to each individual. The targeting tries to take advantage of what 
Amazon knows about you to show you the particular ad that is most likely to appeal to you.

An overview of the service is covered in the [design document](DESIGN_DOCUMENT.md). We encourage you to read that now
before continuing below.

## Project Mastery Tasks

#### Under each mastery task I have linked to parts of the project that are my code.  
### [Mastery Task 1: Filter Out the Noise](tasks/project-mastery-tasks/MasteryTask01.md)

My Contributions:   
- [Class diagram](src/resources/mastery-task1-kindle-publishing-CD.puml)  
- [Sequence diagram](src/resources/mastery-task1-remove-book-SD.puml)  
- [Remove Book](https://github.com/AbeKalovsky/kindle_publishing_service/commit/5431a9b1009d76d2338516e3409f4cbe87655c89#diff-425953d684a72c3bf3cfd03b7640ef448c58a593f6132aa59de3fdd966212fc4)
- [Soft Delete](src/com/amazon/ata/kindlepublishingservice/dao/CatalogDao.java)  

### [Mastery Task 2: Submit to the process](tasks/MasteryTask02.md)

My Contributions:
- [BookPublishRequestManger](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishingRequestManager.java)  
- [SubmitBookForPublishingActivity](src/com/amazon/ata/kindlepublishingservice/activity/SubmitBookForPublishingActivity.java) 

### [Mastery Task 3: Query, query on the wall, don’t load one, get them all!](tasks/MasteryTask03.md)

My Contributions:
- [DynamoDB Query](src/com/amazon/ata/kindlepublishingservice/dao/PublishingStatusDao.java)
- [GetPublishingStatus](src/com/amazon/ata/kindlepublishingservice/activity/GetPublishingStatusActivity.java) 

### [Mastery Task 4: Make a run(nable) for it](tasks/MasteryTask04.md)

My Contributions:
- [BookPublishTask (Runnable)](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishTask.java)
- [BookPublishingRequestManager(Updated for Thread Safety)](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishingRequestManager.java)
- [BookPublishRequest(Updated for Thread Safety)](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishRequest.java)


