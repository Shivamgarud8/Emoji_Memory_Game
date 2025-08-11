# 🧠 Emoji Memory Game

A simple and fun **Memory Matching Game** built with **HTML, CSS, and JavaScript**.  
Match all emoji pairs before the timer runs out!  

---

## 🎯 Features
- 5×10 grid with 25 emoji pairs
- Timer countdown (120 seconds)
- Click 2 cards to reveal emojis
- Matching pairs disappear
- Win or lose message at the end
- Runs on any browser

---

## 📂 Project Structure


memory-game/
├── index.html # Game layout
├── style.css # Game styling
├── script.js # Game logic
└── README.md # Instructions



2️⃣ Install Python 3 (if not already installed)
Amazon Linux:
sudo yum install python3 -y

Ubuntu/Debian:
sudo apt update && sudo apt install python3 -y

Check Version:
python3 --version

3️⃣ Start a Local Web Server
python3 -m http.server 8080



☁️ Running on AWS EC2
1️⃣ SSH into EC2 Instance
ssh -i your-key.pem ec2-user@your-ec2-public-ip
2️⃣ Install Python 3
sudo yum install python3 -y         # Amazon Linux
sudo apt update && sudo apt install python3 -y   # Ubuntu
3️⃣ Upload Files to Server
You can use scp from your local machine:
scp -i your-key.pem -r memory-game ec2-user@your-ec2-public-ip:/home/ec2-user/
4️⃣ Run the Server
cd /home/ec2-user/memory-game
python3 -m http.server 8080
5️⃣ Allow Port 8080 in AWS Security Group
Go to AWS Console → EC2 → Security Groups
Edit inbound rules → Add:
Type: Custom TCP
ort Range: 8080
Source: 0.0.0.0/0
6️⃣ Access in Browser
http://<your-ec2-public-ip>:8080
🛠 Technologies Used
HTML5

CSS3

JavaScript (Vanilla JS)

Python HTTP Server (for local hosting)

