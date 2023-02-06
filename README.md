# h2-Information-security
h2 Goat This is the homework 2 for information security lesson

_________________________________________________________________________________________________________________________________________________________________
x) Read and summarize (This subtask x does not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like)
OWASP: OWASP 10 2021
1. A05:2021-Security Misconfiguration
2. A06:2021-Vulnerable and Outdated Components
3. A03:2021-Injection
4. Any episode from Darknet Diaries.
5. Pick a CVE, and briefly explain it & why it matters
___________________________________________________________________________________________________________________________________________________________________
A05:2021 – Security Misconfiguration

        - The article is focusing on the structural and architectural faults that lead to security risks, and makes clear the need 
        for threat modelling and more secure design. The insecure design is more common than we might believe it is, and every year 
        leads to massive data leaks and account compromisation. As a rule we can learn that an insecure design can not be fixed by a 
        secure implementation, as by definition it needs security controls that we never created. Factors such as insufficient business 
        risk profiling lead to the failure of a system that we are unable to determine the level of security needed.

        - By determining how exposed an account, an app, a website will be, we can assess the importance and the requirements of the 
        security system that will be implemented. Secure design by term is the methodology to constantly evaluate the threats and prevent 
        any known attack, but also to document all the vulnerabilities.
        
        - Prevention is the greatest work, hence our entire career will be successful if we are able to work proactively and not after 
        the "damage is done". By integrating a security language, by establishing and using secure libraries, by segregating tier layers
        on the system and the network and by threat modelling for critical processes we are able to keep our systems safe. 
        
A06:2021 – Vulnerable and Outdated Components

        Vulnerable components are a known great issue of our days that concern outdated systems which are unable to update, 
        test and assess the risk. 
        
        Vulnerability reasons:
        The OS is outdated and i missing critical patches, or it is unsupported. The clients or the servers are not scanned 
        regularly for threats. In general if we are not aware of the current threats, or if our practices do not align with 
        the correct use of the company that produces the componets, there is a great chance to be victimized. 
        
        Sensible practices will be to keep our components updated and obtain them only from the official sources over secure 
        links. Also we must remove all the unused dependencies and unnecessary features. 
        
A03:2021 – Injection

        Vulnerabilities and data breaches happen when user-supplied data is not filtered, validated, or sanitized from the 
        application. Hostile data is used within object rational mapping, and is directly used or concatenated. 
        Parts of prevention include automated testing, using a safe API, 
        
___________________________________________________________________________________________________________________________________________________________        
Darknet Diaries: Ep126 REvil.
__________________________________________________________________________________________________________________________________________________________________

I chose the episode with the REvil ransomware. The story begins with a wild scam story in the US, trying to show us how easy 
it is for a scam to emerge out of nowhere. It takes very little energy and a twisted mind, of course with the main goal being 
the money.
        
REvil ransomware emerged back in 2019, from another variant named GandCrab, and GandCrab is a group that cybersecurity 
specialists call big game hunting. GandCrab is the name of a malware that encrypts the contents of the harddrive and posts 
a message asking for an amount of money in order to provide the user with a password to decrypt the drive. GandCrab, was 
a ransomware that didn't target normal house users but was targeting big companies with big revenue, resulting big money. 
GandCrab though still needed a way in for these big companies and the fact that there are people around the net willing to 
sell their credentials to give access to big companies that they used to work with is unbelievable. 

GandCrab eventually, evolved to ransomware as a service. You could buy the ransomware online in order to extort a company that 
you know and have access to, and then get your share from the extorted money. In the darkm forums it seemed that the origin of 
the ransomware was russian. The US has no jurisdiction in Russia in order to chase or arrest cyber-criminals. And one day out
of nowhere, it disappeared mentioninh to their website that the company retires. But they came back bigger, with the ransomware 
maleware REvil.

REvil in the first phase was doing what all malware is doing, changing the wallpaper, delete the backups, etc. The bizzare to this 
case was that the ransomware was making a language check and if the computer was located in a country of the ex-Soviet Union the 
ransomware would simply exit. Ransomware REvil was in a way the best malware developed. The group decided after GandCrab that they 
will no longer operate the attacks but they will sell it as a service. The customer would break into a company and then drop the REvil
to infect the network. AFter that was the REvil group's job to do the rest.
___________________________________________________________________________________________________________________________________________________________________
b) Injected. Solve WebGoat:

A1 Injection (intro)                     

As an introduction to the subject we see that this lesson described what SQL is and how we can manipulate it in order to perform tasks 
that were not the original intent of the developer. 
After the task we will be able to demonstrate knowledge on:
        DML, DDL and DCL
        String SQL injection 
        Numeric SQL injection 
        Violation of the CIA triad.
What is SQL?

        It is a standardized programming language which is used for managing relational databases and performing various operations on 
        the data in them. As a database we name the collection of data which is organized into rows, columns, tables and it is indexed 
        to make it easier to find information. The three main protection goals in information security are confidentiality, integrity 
        and availability, are considered the three most crucial components of information security. 
        
Task 1: On the the very first tasks we have to create an SQL query to manage to print the department of a specific employee.

        SELECT department FROM employees WHERE last_name='Franco';
        
Task 2: What is DML?
        
        Data Manipulation Language, deals with the manipulation of data and includes the most common SQL statements such as SELECT, INSERT, 
        UPDATE, DELETE etc,and it is used for requesting a result set of records from database tables (select), adding(insert), 
        deleting and modyfing (update) data in a database. By using DML type for an SQL injection the hacker will violate two of the three 
        CIA triad protection goals: confidentiality and integrity (update). (Only authorized people can read the data.)
        
        - DML commands are used for storing, retrieving, modyfying, and deleting data.
        - SELECT - retrieve data from a DB
        - INSERT - insert data in a table
        - UPDATE - updates existing data within a table
        - DELETE - delete all records from a DB table
        
        Example: 
        SELECT phone 
        FROM employees
        WHERE userid = 96134;
        - This statement delivers the phone number of the employee with the used id 96134.
        
Task: We have to change the department of an employee, thus to UPDATE the DB
        
        UPDATE employees SET department='Sales' WHERE last_name='Barnett'
        
Task 3: What is DDL?

        Data definition language, includes commands for defining data structures, especially database schemas which tell how the data 
        should reside in the database. By using the DDL for the SQL injection the user violates the integrity (alter) and the availability 
        (drop) (Only authorized users can manipulate data such as deleting/changing.) 
        
        DDL commands are used for creating, modifying, and dropping the structure of database objects.
        CREATE - to create a database and its objects like (table, views..)
        ALTER - alters the structure of the existing database
        DROP - delete objects from the database 
        
        Example:
        CREATE TABLE employees (
        userid varchar(6) not null primary key,
        first_name varchar(20),
        last_name varchar(20),
        salary varchar(10),
        auth_tan varchar(6)
        );

Task: We have to add a column "Phone" to the already existing table. So, by taking as an example the query we used to create the table we have:

        ALTER TABLE employees ADD phone varchar(20)

Task 5: What is DCL?
        Data control language, is used to create priviledges to allow users to access and manipulate a database. By SQL injection which uses DCL type, the perpetrator violates the confidentiality (grant) and the availability (revoke)(Unwanted people could grand themselves admin priviledges or revoke the admin rights from an administrator.)
        
        DCL commands are used for providing security to database objects
        GRANT - allow users access priviledges to the database
        REVOKE - withdraw users access priviledges given by the GRANT command
        
        Example:
        GRANT CREATE TABLE
        TO operator;
        This statement gives all users of the operator-role the priviledge to create new tables in the databese.
Task: Grant the usergroup "UnauthorizedUser" the right to alter tables.

        GRANT ALTER TABLE 
        TO UnauthorizedUser

Task is done. I will write the report soon :)
___________________________________________________________________________________________________________________________________________________________________
a) Sequel. Solve SQLZoo:
0 SELECT basics
2 SELECT from World, from first subtask to 5 "France, Germany, Italy"
___________________________________________________________________________________________________________________________________________________________________

0.basics is done with ease, and the learning outcome is:

WHERE: 

    SELECT population FROM world 
    WHERE name = 'Germany'

IN:

    SELECT name, population FROM world
    WHERE name IN ('Sweden', 'Norway', 'Denmark');
    
BETWEEN:

    SELECT name, area FROM world
    WHERE area BETWEEN 200000 AND 250000
    
Task 5:

![5](https://user-images.githubusercontent.com/113516460/215791516-5da69ec2-e67a-4991-8029-b7d11d8c2652.JPG)




___________________________________________________________________________________________________________________________________________________________________
m) Voluntary bonus: Pick your tasks from SQLZoo 1, 3-9.
___________________________________________________________________________________________________________________________________________________________________
I decided to do all the tasks from the SQLZoo 1-13.

Task1:

![1](https://user-images.githubusercontent.com/113516460/215804042-91eed3d7-6254-4f9d-a999-7d7c481877d1.JPG)

Task2:

![2](https://user-images.githubusercontent.com/113516460/215804074-d174bf09-c016-4cd8-8e66-aa4717c0918f.JPG)

Task3:

![3'](https://user-images.githubusercontent.com/113516460/215804175-0fdc28c8-057b-46c6-a8f5-8a06d1a5f6ae.JPG)

Task4:

![4](https://user-images.githubusercontent.com/113516460/215804227-bb1f4f02-e878-4091-a767-56808946cfba.JPG)

Task6:

![6](https://user-images.githubusercontent.com/113516460/215804288-a7681d99-cf35-4a7d-898d-e19b3e26fd63.JPG)

Task7:

![7](https://user-images.githubusercontent.com/113516460/215804332-1b83b5de-3dc6-43b7-a0b5-1f1d03217fe5.JPG)

Task8:

![8](https://user-images.githubusercontent.com/113516460/215804365-cd40be67-463e-44e0-bad6-71e08960ae19.JPG)

Task9:

![9](https://user-images.githubusercontent.com/113516460/215804434-02df1246-8854-4326-9a0a-c7eb7773340e.JPG)

Task10:

![10](https://user-images.githubusercontent.com/113516460/215804452-3aea2bd5-5184-4a07-9d46-829d8762a89d.JPG)

Task11:

![11](https://user-images.githubusercontent.com/113516460/215804481-c471db74-a539-41c7-813b-f65cd6e45685.JPG)

Task12:

![12](https://user-images.githubusercontent.com/113516460/215804524-8a74010c-6b15-4b75-bb4c-e2a9ca32747f.JPG)

Task13:

![13](https://user-images.githubusercontent.com/113516460/215804586-23225f58-deae-427b-ad9b-fa671efcdda8.JPG)

The test was also done:

![quiz](https://user-images.githubusercontent.com/113516460/215805012-8dc6e050-cffa-4403-a4f9-93cb2bea6158.JPG)

SOURCES
_______________________________________________________________________________________________________________________________________________________________
        https://www.redhat.com/en/topics/security/what-is-cve
        https://owasp.org/Top10/A04_2021-Insecure_Design/
        https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/
        https://owasp.org/Top10/A03_2021-Injection/
        https://darknetdiaries.com/
        https://darknetdiaries.com/transcript/126/
        
