## PASHI Documentation ##
**PASHI -> Portland Affordable, Safe Housing Initiative**  
*"Giving those in need an ability to find, not only affordable, but SAFE housing in the City of Portland."*

### Project Information

Obtaining affordable housing in the City of Portland (CoP) is challenging; finding affordable housing that is also safe and desirable is even more challenging especially for those in need.  This app is designed to allow users to view their options and make informed decisions based on a location factoring in its safety for themselves and/or families.

### Project Framework

&ensp; Section 1.  Administration.  Setting up project admin, mapping project, etc.  
&ensp; Section 2.  App Framework.  Building out shell and UXI.  Ensuring user login works.    
&ensp; Section 3a.  Prepping Datasets.  Building out datasets with appropriate data.  
&ensp; Section 3b.  App Backend.  Building out models, logic, and API.    
&ensp; Section 4.  App Frontend.  Add functionality to the UXI - make input/output functions usable.  
&ensp; Section 5.  Formatting UX.  Final formatting for overall website  and polished UX.  
&ensp; Section 6.  Testing/Rollout.  Independent testing. Fix edge cases, bugs.  

### Project Milestones


  | Week 1                  | Week 2                        | Week 3                          | Week 4                        |
  | ----------------------- | ----------------------------- | ------------------------------- | ----------------------------- |
  | S1. Admin Start/Finish  | S2. (MVP) Framing Finish      | S3b. (MVP) Backend Finish       | S5. (MVP) UX Dev Start/Finish |
  | S2. Framing Start       | S3a. Prep Data Start/Finish   | S4. (MVP) Frontend Start/Finish | S6. Testing/Rollout           |
  |                         | S3b. Backend Start            |                                 |                               |

### S1. Administration

**Tasks:**

  - [x] a. Intro to Github and project management
  - [x] b. Buildout hosting area / Set up file structure
  - [x] c. Setup app documentation and formatting style (readme.md)
  - [x] d. Create project milestone framework
  - [x] e. White board project
  - [x] f. Identify data required
  - [ ] g. Model the models
  - [x] h. Naming conventions/general coding notes

**Notes on tasks:**

a. Utilizing modified Agile Framework with MVP milestones at set stages.  

f. Datasets
   - Primary:  
     - Crime_Data *Obtained from CoP Crime Datasets  
     - Housing_Data *Obtain from CoP or Oregon State data website (API)  
   - Secondary:    
     - Zip-code info associated with unique Portland Areas  
     - Zip-code info associated with housing data addresses  

h. Code naming convention  
   - Variables (single value):  camelCase  
   - Lists/Arrays:  name_name  

### S2. App Framework

  **Tasks:**
   - [ ] a. Build django framework in project folder
   - [ ] b. Build out first model, test  
   - [ ] c. Build CSS Structure with place holders
   - [ ] d. Build User functionality (login)

### S3a. Dataset Prep

  **Tasks:**
  - [ ] a. Pull datasets from CoP or figure out if an API call would work
  - [ ] b. Pull zip code dataset based on Portland neighborhoods
  - [x] c. Pull 2020 crime dataset from CoP crime data site and evaluate
  - [ ] d. Build out crime_index as noted in methodology
  - [ ] e. Build out housing_data as noted in methodology


  **Crime Data Methodology:**
```
-> raw Crime Data -> scrub for anomalies and null data  
-> merge data with zip code dataset   
-> rank Crimes based on severity (i.e. assign value -> new field)   
-> add up value of crimes based on zip codes (intValue) -> new list crime_index

**crime_index = [{'id' : idNum, ‘zipCode#’: intValue,}]**  
(better name? safety_rank?)  
```
  **Housing Data Methodology:**  
```  
-> raw Housing Data (or API) -> scrub and sanitize  
-> merge data with zip code data based on addresses (create new field)

**housing_data = [{'id' : idNum, 'zipCode' : 'zipCode#', etc., }]**
```  

**Integrity and accuracy:**  
Testing ongoing at each stage of manipulation to ensure data integrity.  

**Discussion on dataset logic**:  
The crime_index could be derived in a number of ways; however, for the purposes of this app/project, the value of the offense type will be given a value of 1-20 (i.e. murder = 20, parking violation = 1) and then summed by zip-code to develop an ‘index’.  This methodology could potentially skew data (in a circumstance of a high murder rate, low overall occurance of crime), however, it appears to make the most sense over counting the number of crimes in an area (i.e. averaging data based on the severity of crime vs. treating all crimes as equal).  

### S3a. Backend

  **Tasks:**
  - [ ] a. Build out Models
  - [ ] a. Build out API
  - [ ] a. Test models

  **Models**

  ```
  crime_index = [
    {'id' : sysAssigned,
    ‘zipCode#’: intValue,}
  ]
  ```
  ```
  housing_data = [
    {'id' : idNum,
    'zipCode' : 'string',
    'address' : 'string',
    'phoneContact' : 'string',
    }
  ]
  ```
  ```
  user_data = [
    {'id' : sysAssigned,
    'userName : 'string',
    'userPwd : sysAssigned,
    'firstName' : 'string',
    'lastName' : 'string',
  }
  ]
  ```
  ```
  join_table = [
    {'id' : sysAssigned,
    'user_data.id' : integer,
    'housing_data.id' : integer,
    'userNotes' : 'string',
    }
  ]
  ```





  | First Header  | Second Header |
  | ------------- | ------------- |
  | Content Cell  | Content Cell  |
  | Content Cell  | Content Cell  |
