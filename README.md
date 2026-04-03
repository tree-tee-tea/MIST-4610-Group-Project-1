
Group 5 MIST 4610 Group Project 1
## Team Name: Sp26_61608_Group 5
## Team Members:
 Yachana Shah - https://github.com/tree-tee-tea/MIST-4610-Group-Project-1 
Bella Fraker - https://github.com/bellafraker/Team-5-MIST-4610-Group-Project-1
Tim Adewoye: https://github.com/timiadewoye/MIST-4610-Group-5-Project-1-Tim-Adewoye
Lauren Cushings: https://github.com/laurencushing/Team-5-MIST-4610-Group-Project-1
Brandon Sevel: https://github.com/BrandonSevel/MIST-4610-Group-5-Project-1 
Benjamin Saunders https://github.com/BensOnPluto/Team-5-MIST4610-Project1

## Problem Description

The task is to model and build a relational database for Athens Pulse Fitness operations, focusing on coordinating members, trainers, classes, and studio rooms. The database manages memberships, trainer assignments, class scheduling, and attendance while maintaining clear relationships between all entities. It enforces key business rules, including room capacity limits and membership tier restrictions, such as limiting Basic members to four classes a month while Unlimited members have unrestricted access. Attendance tracking must also ensure members are marked as “No-Show” if they fail to check in at least five minutes before class begins. The finished system supports meaningful business insights, member attendance trends, and facility usage efficiency.
## Data Model

### Explanation of Data Model

Our model represents a fitness studio management system. The Members entity is our core entity and represents each individual who uses the studio. It includes information such as their name and contact information. Members and Memberships have a many-to-many relationship. To resolve this, we created the membershipLogs table as an associative entity to track these connections.

Another major part of the model is the relationship between Members and Trainers. Because of the many-to-many relationship between them, we created the associative entity trainingLogs. This table allows the studio to keep track of personal training sessions and the connections between clients and staff.

The model also includes a Classes entity, which represents the different classes offered by the fitness studio, such as yoga, cycling, or strength training. Since many members can attend a class, and trainers teach those classes in specific rooms, we used the classLogs entity to connect Classes, Members, Trainers, and studioRooms. This allows the system to record each class instance, who attended it, who taught it, and where it took place.
Lastly, the model includes the studioRooms and Equipment entities to represent the physical resources of the studio. A studio room may contain many pieces of equipment, and the same type of equipment may appear in multiple rooms, so we created the equipmentInventory table as the associative entity between them. Overall, this model captures both the customer-facing side of the fitness studio, such as memberships and classes, and the operational side, such as trainers, rooms, and equipment.

### Image of Data Model

### Data Dictionary

#### Tables

## Queries

### Query 1

This query identifies the boutique gym’s highest‑demand classes by measuring total attendance across all logged sessions. By aggregating participation counts for each class and seeing them from most to least attended, the gym can quickly see which offerings attract the most members. These insights support strategic decisions such as reallocating studio space, adjusting instructor schedules, increasing class frequency, or investing more resources into the formats that consistently drive engagement.

SELECT c.className, COUNT(cl.Members_memberID) AS attendance
FROM classLogs cl
JOIN Classes c ON cl.Classes_classID = c.classID
GROUP BY c.className
HAVING COUNT(cl.Members_memberID) > 1
ORDER BY attendance DESC;





