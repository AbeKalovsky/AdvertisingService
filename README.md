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
- [TargetingEvaluator](https://github.com/AbeKalovsky/advertising_service/commit/e9c551661b0e0d31a2c29cea005e361ed92add75#diff-02dc29df07086cb92039935496cf1f687b78fda8da17ea97a0634412dd2d042d)
- [AddTargetingGroupActivity(Updated to use Streams)](https://github.com/AbeKalovsky/advertising_service/commit/e9c551661b0e0d31a2c29cea005e361ed92add75#diff-b75ca21099df519fe8211d569ede706ec1e35f3070ac837d1fbe516abc2a7a50)  
- [AdvertisementSelectionLogic(Updated to use Streams)](https://github.com/AbeKalovsky/advertising_service/commit/e9c551661b0e0d31a2c29cea005e361ed92add75#diff-36f50daf88514c690c1d9339374398391757eec05677bedfbe6d07d6b5c8e7f8)  

  

### [Mastery Task 2: Concurrent Tasks](tasks/project-mastery-tasks/MasteryTask02.md)

My Contributions:
- [TargetingEvaluator(Updated for multi-threading)](https://github.com/AbeKalovsky/advertising_service/commit/508d29f6e5a52733690128f32f944c10297e3381#diff-02dc29df07086cb92039935496cf1f687b78fda8da17ea97a0634412dd2d042d)  


### [Mastery Task 3: Query, query on the wall, don’t load one, get them all!](tasks/MasteryTask03.md)

My Contributions:
- [DynamoDB Query](src/com/amazon/ata/kindlepublishingservice/dao/PublishingStatusDao.java)
- [GetPublishingStatus](src/com/amazon/ata/kindlepublishingservice/activity/GetPublishingStatusActivity.java) 

### [Mastery Task 4: Make a run(nable) for it](tasks/MasteryTask04.md)

My Contributions:
- [BookPublishTask (Runnable)](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishTask.java)
- [BookPublishingRequestManager(Updated for Thread Safety)](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishingRequestManager.java)
- [BookPublishRequest(Updated for Thread Safety)](src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishRequest.java)


