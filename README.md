# AWS Web Server Lab

---

## 1. Create a Key Pair


<!-- Image: create-keypair.png -->
![Screenshot 2025-06-11 121751](https://github.com/user-attachments/assets/d3de4f8a-4abb-454f-af7c-6a45521d8cb7)


---

## 2. Build Your VPC



<!-- Image: create-vpc.png -->
![Screenshot 2025-06-11 121808](https://github.com/user-attachments/assets/5cdfbb99-1252-42dc-afea-a863800a7c15)


---

## 3. Make a Public Subnet



<!-- Image: create-subnet.png -->
![Screenshot 2025-06-11 122033](https://github.com/user-attachments/assets/ec2bd77d-d60a-4fb2-905d-e9a694a12b94)


---

## 4. Attach an Internet Gateway



<!-- Image: attach-igw.png -->
![Screenshot 2025-06-11 122254](https://github.com/user-attachments/assets/53d34587-9305-4a0c-a9c5-8c20bd2b6aeb)


---

## 5. Set Up a Route Table



<!-- Image: route-table.png -->
![Screenshot 2025-06-11 122656](https://github.com/user-attachments/assets/5610e301-bdd1-4662-8eea-6a762cf18f8e)


---

## 6. Create a Security Group



<!-- Image: security-group.png -->
![Screenshot 2025-06-11 123453](https://github.com/user-attachments/assets/c15a96a3-068c-44c1-abeb-b42be113a152)

---

## 7. Launch Your EC2 Server

Time to start your server!

* Click **Launch instance**.

![Screenshot 2025-06-11 133641](https://github.com/user-attachments/assets/5e147ca7-8b1d-4983-b66d-6c060078ffe5)


---

## 8. Check Your Server



<!-- Image: test-server.png -->
![Screenshot 2025-06-11 133617](https://github.com/user-attachments/assets/d2c42d6a-cf66-404c-9a38-d82e0a4f50b4)


---

## 9. Clean Up

1. Terminate the EC2 instance.
2. Delete the EBS volume.
3. Detach & delete the Internet Gateway.
4. Delete the Subnet.
5. Delete the VPC.
6. Delete the Security Group and Key Pair.

<!-- Image: cleanup.png -->
![Screenshot 2025-06-11 134908](https://github.com/user-attachments/assets/e22873cc-3499-408a-bb5c-6a07cd41a3ea)

## INSTANCES 

![Screenshot 2025-06-11 155344](https://github.com/user-attachments/assets/47f2bfe9-c4f3-485e-b7b6-17206fefdc58)

Absolutely! Here’s a **beginner-friendly README.md** for your GitHub submission. It’s written step-by-step, with clear instructions, and places for screenshots/images.
You can copy and edit the image links as you upload your screenshots.

---

# AWS Two-Tier Web Application Infrastructure – Assignment (HOME TAKE AWAY ASSINGMENT)



---

## Architecture Diagram

*(Upload your architecture diagram here if you have one!)*

```
[ INTERNET ]
     |
[ Internet Gateway ]
     |
 [VPC: 10.10.0.0/16]
   |               |
[Public Subnet]  [Private Subnet]
   |               |
[Web Server]    [DB Server]

```
![ChatGPT Image Jun 13, 2025, 05_51_37 PM](https://github.com/user-attachments/assets/435223a5-fb33-482f-b978-ca7d5d7f479a)


---

## Steps

### Part 1: Network Foundation

1. **Create a VPC**

   * Name: `two-tier-vpc`
   * CIDR: `10.10.0.0/16`

2. **Create Subnets**

   * Public Subnet: `public-subnet-1`, CIDR `10.10.1.0/24`
   * Private Subnet: `private-subnet-1`, CIDR `10.10.2.0/24`

3. **Create and Attach an Internet Gateway**

   * Attach to your VPC.

4. **Configure Route Tables**

   * Public Subnet: Route `0.0.0.0/0` to Internet Gateway.
   * Private Subnet: Use default (no outbound internet).

---

### Part 2: Security Groups

1. **webapp-sg**

   * Inbound HTTP (80): `0.0.0.0/0`
   * Inbound SSH (22): *Your IP only*

2. **database-sg**

   * Inbound MySQL (3306): *Only from webapp-sg (Security Group ID)*
   * No inbound SSH or public access.

---

### Part 3: Launching EC2 Instances

1. **Web Server**

   * Type: `t2.micro`
   * Name: `Web-Server`
   * Subnet: `public-subnet-1`
   * Auto-assign Public IP: **Enabled**
   * Security Group: `webapp-sg`
   * User Data: *(Install web server script)*

2. **DB Server**

   * Type: `t2.micro`
   * Name: `DB-Server`
   * Subnet: `private-subnet-1`
   * Auto-assign Public IP: **Disabled**
   * Security Group: `database-sg`

---

### Part 4: Verification and Testing

1. **Web-Server Access:**

   * Open browser to the public IP of `Web-Server` (should show your website).

2. **SSH Test:**

   * SSH into `Web-Server` using its public IP.

3. **Ping DB-Server:**

   * From `Web-Server`, run:

     ```bash
     ping <private_ip_of_db_server>
     ```



## Screenshots

> **Replace the image links below with your own screenshots**

![Screenshot 2025-06-12 004607](https://github.com/user-attachments/assets/ddba878c-7311-4907-9273-3631017f050d)


![Screenshot 2025-06-12 005006](https://github.com/user-attachments/assets/1df03725-a3f6-4d69-b9e4-ed2fbd971a74)

![Screenshot 2025-06-12 005136](https://github.com/user-attachments/assets/ee9beee6-fcde-4e40-822e-36c139aa898d)

![Screenshot 2025-06-12 005248](https://github.com/user-attachments/assets/4a707fcd-cbe2-4323-a75a-2c12c2255bf8)

![Screenshot 2025-06-12 005627](https://github.com/user-attachments/assets/333a2b61-fa98-4cc5-85ea-89e4fc8f3dbb)

![Screenshot 2025-06-12 005657](https://github.com/user-attachments/assets/86ec8c5b-8a8c-4f52-a580-7f5eabfdc6ad)

![Screenshot 2025-06-12 010114](https://github.com/user-attachments/assets/a6ded356-a9c3-48d5-9b11-0cc5fb1e812f)

![Screenshot 2025-06-12 010925](https://github.com/user-attachments/assets/424a4257-8502-4af6-bd7c-bc2aed7dc853)

![Screenshot 2025-06-12 012650](https://github.com/user-attachments/assets/a93e0e37-5908-4c87-918b-ad091aa55087)

![Screenshot 2025-06-12 012709](https://github.com/user-attachments/assets/4515d6a1-567d-4934-a087-3b7c190d6cae)

![Screenshot 2025-06-12 014924](https://github.com/user-attachments/assets/8857e1c8-b139-46e9-9a89-38ca5dcf6143)

![Screenshot 2025-06-12 015043](https://github.com/user-attachments/assets/e17f034c-de2d-4fd3-b79e-8298e76b29fe)

![Screenshot 2025-06-12 020035](https://github.com/user-attachments/assets/fc2584a1-92e1-471c-bb5d-ae39e1b73009)

![Screenshot 2025-06-12 020711](https://github.com/user-attachments/assets/1678eb3e-173c-4c1a-8959-3af38a5b5b25)


## CLEANUP


![Screenshot 2025-06-12 020711](https://github.com/user-attachments/assets/1678eb3e-173c-4c1a-8959-3af38a5b5b25)

![Screenshot 2025-06-12 022429](https://github.com/user-attachments/assets/9515d449-85dd-49f7-a1b2-9404210a3ce8)



---



