 
# Flask App with MySQL Docker Setup

This is a simple Flask app that interacts with a MySQL database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend.

## Prerequisites

Before you begin, make sure you have the following installed:

- Docker
- Git (optional, for cloning the repository)

## Setup

1. Clone this repository (if you haven't already):

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```

2. Navigate to the project directory:

   ```bash
   cd your-repo-name
   ```

3. Create a `.env` file in the project directory to store your MySQL environment variables:

   ```bash
   touch .env
   ```

4. Open the `.env` file and add your MySQL configuration:

   ```
   MYSQL_HOST=mysql
   MYSQL_USER=your_username
   MYSQL_PASSWORD=your_password
   MYSQL_DB=your_database
   ```

## To run this two-tier application in docker

- First create a docker image from Dockerfile
```bash
docker build -t flaskapp .
```

- Now, make sure that you have created a network using following command
```bash
docker network create twotier
```

- Attach both the containers in the same network, so that they can communicate with each other

i) MySQL container 
```bash
docker run -d --name mysql -v mysql-data:/var/lib/mysql -v ./message.sql:/docker-entrypoint-initdb.d/message.sql --network=twotier -e MYSQL_DATABASE=mydb -e MYSQL_USER=root -e MYSQL_ROOT_PASSWORD="admin" -p 3360:3360 mysql:5.7
```
ii) Backend container
```bash
docker run -d --name flaskapp -v mysql-data:/var/lib/mysql -v ./message.sql:/docker-entrypoint-initdb.d/message.sql --network=twotier -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=admin -e MYSQL_DB=mydb -p 5000:5000 flaskapp:latest
```

## Notes

- Make sure to replace placeholders (e.g., `your_username`, `your_password`, `your_database`) with your actual MySQL configuration.

- This is a basic setup for demonstration purposes. In a production environment, you should follow best practices for security and performance.

- Be cautious when executing SQL queries directly. Validate and sanitize user inputs to prevent vulnerabilities like SQL injection.

- If you encounter issues, check Docker logs and error messages for troubleshooting.



## 
## More to be updated -  Deployment on Kubernetes



First Response (Professional and Concise):
Successfully Handled Disaster Recovery (DR) for Premium Clients: Managed DR processes independently, showcasing expertise and reliability, while also training and mentoring colleagues to build team capability.

Architectural and Functional Mastery of FISCD: Gained a comprehensive understanding of the FISCD architecture and trade flow within its components, enabling you to deliver a reverse knowledge transfer session for colleagues.

Automation Initiatives and Operational Efficiency:

Designed and implemented a Trade Volume Report generator for a premium client.
Developed scripts to automate sanity checks for the CIMB client, reducing average sanity time from 20 minutes to 5 minutes daily.
Automated morning checks for CV servers, significantly decreasing manual effort and improving operational efficiency.
Second Response (Professional with Human Touch):
Driving Disaster Recovery (DR) Success for Premium Clients: I successfully managed DR processes for premium clients with minimal reliance on senior guidance, demonstrating independence and expertise. Alongside this, I took pride in training and mentoring a colleague, ensuring our team is better equipped for future challenges.

Deepening Expertise in FISCD: This year, I delved deeper into the FISCD architecture and gained valuable insights into its working and trade flow across components. Sharing this knowledge through a reverse KT session with the team was a fulfilling experience, contributing to our collective understanding.

Boosting Efficiency through Automation:

Designed a Trade Volume Report generator tailored for a premium client’s needs.
Created an automated sanity check script for the CIMB client, reducing daily sanity check time from 20 minutes to just 5 minutes.
Developed and deployed a script to automate CV server morning checks, significantly cutting down manual efforts and streamlining operations.
Key Differences:
Tone:

The first response is more direct, concise, and formal, emphasizing accomplishments without personalization.
The second response is more conversational and relatable, highlighting your pride and satisfaction in your achievements.
Engagement:

The second response conveys a sense of ownership, personal growth, and collaboration, which may resonate better in a one-on-one professional discussion.
