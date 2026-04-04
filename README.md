# Team 5 MIST 4610 Group Project 1
## Team Name
61608 Group 5


## Team Members
1. Bella Fraker @https://github.com/bellafraker
2. Tim Adewoye @https://github.com/timiadewoye
3. Yachana Shah @https://github.com/tree-tee-tea
4. Lauren Cushings @https://github.com/laurencushing 
5. Brandon Sevel @https://github.com/BrandonSevel
6. Benjamin Saunders @https://github.com/BensOnPluto

## Problem Description
The task is to model and build a relational database for Athens Pulse Fitness operations, focusing on coordinating members, trainers, classes, and studio rooms. The database manages memberships, trainer assignments, class scheduling, and attendance while maintaining clear relationships between all entities. It enforces key business rules, including room capacity limits and membership tier restrictions, such as limiting Basic members to four classes a month while Unlimited members have unrestricted access. Attendance tracking must also ensure members are marked as “No-Show” if they fail to check in at least five minutes before class begins. The finished system supports meaningful business insights, member attendance trends, and facility usage efficiency.
## Data Model
Our model represents a fitness studio management system. The Members entity is our core entity and represents each individual who uses the studio. It includes information such as their name and contact information. Members and Memberships have a many-to-many relationship. To resolve this, we created the membershipLogs table as an associative entity to track these connections.

Another major part of the model is the relationship between Members and Trainers. Because of the many-to-many relationship between them, we created the associative entity trainingLogs. This table allows the studio to keep track of personal training sessions and the connections between clients and staff.

The model also includes a Classes entity, which represents the different classes offered by the fitness studio, such as yoga, cycling, or strength training. Because classes occur multiple times and can have many attending members, we used the classLogs entity as a central associative table to connect Classes, Members, Trainers, and studioRooms. This allows the system to record each class instance, who attended it, who taught it, and where it took place. Each of these entities has a one-to-many relationship with classLogs, as one class, member, trainer, or room can appear in many class instances.

Lastly, the model includes the studioRooms and Equipment entities to represent the physical resources of the studio. A studio room may contain many pieces of equipment, and the same type of equipment may appear in multiple rooms, so we created the equipmentInventory table as the associative entity between them.

Overall, this model captures both the customer-facing side of the fitness studio, such as memberships and classes, and the operational side, such as trainers, rooms, and equipment.
<img width="620" height="459" alt="Screenshot 2026-04-01 at 4 38 13 PM" src="https://github.com/user-attachments/assets/f5711b9b-ab73-486f-b52b-610f7167bedd" />
## Data Dictionary
<img width="662" height="293" alt="Screenshot 2026-04-01 at 8 30 37 PM" src="https://github.com/user-attachments/assets/35ea8bf7-5fd2-43b4-9fe2-7e63e0a86345" />

<img width="684" height="238" alt="Screenshot 2026-04-01 at 8 31 16 PM" src="https://github.com/user-attachments/assets/1a1e388d-a6b2-4f47-9da4-04c54c68ada6" />

<img width="669" height="456" alt="Screenshot 2026-04-01 at 8 32 47 PM" src="https://github.com/user-attachments/assets/d98a9e95-f57c-42da-80f7-10cfb7b0c5f3" />

<img width="661" height="194" alt="Screenshot 2026-04-01 at 8 34 08 PM" src="https://github.com/user-attachments/assets/b030c66d-b48c-4a0d-96d6-b54352511b35" />

<img width="653" height="305" alt="Screenshot 2026-04-01 at 8 52 13 PM" src="https://github.com/user-attachments/assets/9079c607-818d-4388-8127-eb12002a3aef" />

<img width="693" height="389" alt="Screenshot 2026-04-01 at 8 53 34 PM" src="https://github.com/user-attachments/assets/086fcc63-d0cf-479f-b39b-5b6d3f9bfc41" />

<img width="696" height="215" alt="Screenshot 2026-04-01 at 8 52 42 PM" src="https://github.com/user-attachments/assets/1d0a6f5e-83d8-43d5-86a8-4bcbcf75b788" />

<img width="705" height="299" alt="Screenshot 2026-04-01 at 9 10 12 PM" src="https://github.com/user-attachments/assets/2e2be027-78fb-458a-8e91-64e6decd4dc3" />

<img width="708" height="336" alt="Screenshot 2026-04-01 at 9 10 25 PM" src="https://github.com/user-attachments/assets/c30e5ca6-6307-45b6-b35f-2a4bcc2dacc7" />

<img width="713" height="276" alt="Screenshot 2026-04-01 at 9 10 44 PM" src="https://github.com/user-attachments/assets/7ad1a074-f380-4a5e-bf12-ffec97036dcb" />


## Queries

<img width="554" height="318" alt="Screenshot 2026-04-03 at 10 24 08 PM" src="https://github.com/user-attachments/assets/290761d3-fd61-40ee-8acd-562f112ea1ad" />

QUERY 1: 
This query identifies the boutique gym’s highest‑demand classes by measuring total attendance across all logged sessions.
<img width="1250" height="692" alt="Screenshot 2026-04-03 at 6 37 59 PM" src="https://github.com/user-attachments/assets/c556c484-66d5-46ed-b8c3-e975ec4db740" />
By aggregating participation counts for each class and seeing them from most to least attended, the gym can quickly see which offerings attract the most members. These insights support strategic decisions such as reallocating studio space, adjusting instructor schedules, increasing class frequency, or investing more resources into the formats that consistently drive engagement.

QUERY 2: 
This query identifies studio rooms where the number of attendees exceeds the room’s capacity.
<img width="1250" height="666" alt="Screenshot 2026-04-03 at 7 28 35 PM" src="https://github.com/user-attachments/assets/33f70115-607f-4caa-b3ce-86646361f6a7" />
By comparing the number of members attending classes in each studio room to that room’s capacity, the gym can quickly identify instances where rooms are being overfilled. These insights support operational decisions such as reallocating classes to larger rooms, limiting class sizes, adjusting scheduling to reduce overcrowding, or ensuring compliance with safety and comfort standards.

QUERY 3: 
This query identifies the trainers in descending order who have taught the most classes.
<img width="1250" height="566" alt="Screenshot 2026-04-03 at 7 36 17 PM" src="https://github.com/user-attachments/assets/5e5cd76a-df8c-475b-89ac-475c68018e93" />
This query identifies the trainers who have taught the most classes by counting the number of class sessions each trainer has conducted in the classLogs table. It groups the results by trainer ID, first name, and last name, and calculates the total number of classes taught by each trainer. The results are then sorted in descending order, so the trainers with the highest number of classes appear at the top. This allows for easy identification of the most active or in-demand trainers based on class instruction. 

QUERY 4: 
This query identifies the equipment available in each studio room by linking rooms and equipment through the inventory table.
<img width="1250" height="551" alt="Screenshot 2026-04-03 at 7 57 50 PM" src="https://github.com/user-attachments/assets/13df5f8b-5bdb-423f-ae6d-1ac9d8fc77a7" />
This query shows what equipment is assigned to each studio room. It links each studio room to the equipment stored in it using the equipmentInventory table, which acts as a bridge between the two. The query displays the studio ID along with each piece of equipment’s ID, name, and model. These insights help the gym determine which types of classes can be held in each room based on available equipment, and support better planning of class offerings and resource allocation.

QUERY 5: This query lists each member with their membership tier.
<img width="1251" height="530" alt="Screenshot 2026-04-03 at 8 05 17 PM" src="https://github.com/user-attachments/assets/2fe3937a-0f28-4273-8d00-14bcd3d0c588" />
This query lists each member along with their corresponding membership tier by joining the Members, membershipLogs, and Memberships tables. The membershipLogs table acts as a link between members and their memberships, allowing the query to match each member to their assigned membership tier. The result displays the member’s ID, first name, last name, and membership tier. This information helps the gym track which members belong to each membership tier, enforce membership rules such as class limits, analyze the popularity of tiers, and support marketing and upgrade decisions.

QUERY 6: This query identifies which members participated in training sessions by joining the Members and trainingLogs tables.
<img width="1253" height="697" alt="Screenshot 2026-04-03 at 8 41 48 PM" src="https://github.com/user-attachments/assets/c01b0036-4a58-44ce-848c-98606c921b66" />
This query identifies which members participated in training sessions by joining the Members and trainingLogs tables. It matches each member to their corresponding training sessions using their member ID. The result displays each member’s name along with their training session ID, providing a clear view of member participation in personal training activities. This helps us track engagement so we know when to upgrade membership tiers, evaluate demand, and track patterns in participation so we know how to best manage our trainers and trainees. 

QUERY 7: Displays each class session along with the associated member, trainer, class name, and studio room.
<img width="1250" height="690" alt="Screenshot 2026-04-03 at 8 46 20 PM" src="https://github.com/user-attachments/assets/f982ae01-d131-47ee-845e-ce6c65ff5979" />
This query combines data from 5 of our tables to give a full view of what each session looks like. Using this, we are able to correlate members with the trainer, class name, and studio room to the class session they attended. This is useful because it gives the fitness studio a more complete picture of class activity. Instead of only seeing IDs, management can see the actual people, classes, trainers, and rooms involved in each session. This can help with tracking attendance, reviewing trainer workloads, analyzing class popularity, and checking how studio rooms are being used.

QUERY 8: This query identifies how many members belong to each membership tier by joining the Memberships and membershipLogs tables. It counts the number of members per tier and filters out tiers with only one member. This helps the gym understand which membership tiers are most popular and supports decisions around pricing, promotions, and membership offerings.
<img width="1251" height="688" alt="Screenshot 2026-04-03 at 10 19 32 PM" src="https://github.com/user-attachments/assets/3128695a-dc1e-4913-ad46-65299e7558d0" />

QUERY 9: This query counts how many training sessions each trainer has conducted, filtered out any trainers with missing names or specializations. The Group BY aggregates sessions per trainer and the Having clause limits results to only trainers who have logged more than one session. The data displays which trainers are actively working with members. 
<img width="1249" height="687" alt="Screenshot 2026-04-03 at 9 48 12 PM" src="https://github.com/user-attachments/assets/2805c86c-89ff-4f21-82f9-2d93c7465570" />

QUERY 10: This Query groups classes by their type and counts how many classes exist under each type, using REGEXP to ensure the class type contains only valid characters and spaces. The not exists subquery excludes any class that has a log entry with a null member ID, filtering out improperly recorded enrollment records. The having clause then limits results to class types that have at least 1 fully logged class. 
<img width="1252" height="684" alt="Screenshot 2026-04-03 at 9 49 16 PM" src="https://github.com/user-attachments/assets/6a2b097d-72a8-40ee-81f0-cf8eb97c5676" />

## Database Information
Database Name: ns_Sp26_61608_Group 5

Additional Information: Each query listed above is marked in the database using stored procedures which can be called using the following format:Q1, Q2, Q3
