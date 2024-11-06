# Jenkins


 -----------------------------------------------------------------------------------------
**************************jenkins ML_CI_CD**************************  
------------------------------------------------------------------------------------------

* Project link : https://towardsdatascience.com/from-devops-to-mlops-integrate-machine-learning-models-using-jenkins-and-docker-79034dbedf1

* github repo link : https://github.com/xaviervasques/Jenkins

* AWS Amazon linux 5.10/t2.medium/30gb/all-traffic server

      1  sudo yum update -y
      2  sudo yum upgrade -y
      5  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
      22  sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
      23  sudo yum upgrade -y
      24  sudo amazon-linux-extras install java-openjdk11 -y
      26  sudo yum install jenkins -y
      28  sudo systemctl enable jenkins
      29  sudo systemctl start jenkins      (open, public_ip:8080  in browser)
      30  sudo systemctl status jenkins
      31  jenkins --version
      10  sudo yum install git -y
      11  java --version; jenkins --version; git --version
      12  sudo amazon-linux-extras | grep docker
      13  sudo amazon-linux-extras
      14  sudo amazon-linux-extras install docker -y
      15  docker --version
      16  sudo systemctl daemon-reload
      19  sudo cat /var/lib/jenkins/secrets/initialAdminPassword     (paste password in browser)
      20  which git
      21  sudo visudo -f /etc/sudoers.d/filename  (jenkins ALL=(ALL) NOPASSWD: ALL)
      23  pwd
      24  ll
      25  sudo systemctl status docker
      26  sudo systemctl start docker
      27  sudo systemctl status docker
      28  sudo docker image list
      30  sudo docker ps
      31  git init
          git status
          git add .
          git remote add origin <>
      32  vi Dockerfile 
      35  sudo docker build -t my-docker -f Dockerfile .
      37  sudo docker image list
      40  vi train-lda.py
      41  sudo docker image list
      42  sudo docker build -t my-docker-lda -f Dockerfile .
      44  sudo docker ps
      45  sudo docker image list
      46  sudo docker build -t my-docker-automl -f Dockerfile .
      47  sudo docker build -t my-docker-nn -f Dockerfile .
      48  sudo docker image list



create job 

copy and paste in  build steps: select execut shell>> paste below 

-----------------------------------
mlproject
----------------------------------
build steps:


sudo -S cp * /home/ec2-user/


--------------------------------
mlproject2
-----------------------------------

if sudo docker ps -l | grep my-docker-lda
then
	echo "my-docker-lda already build"
else
	echo "my-docker-lda not build"
fi

if sudo grep "clf_lda" /home/ec2-user/train-lda.py
then
	sudo docker run -p 5000:5000 my-docker-lda python3 train-lda.py > result.txt
    sudo cat result.txt
fi

res=$(sudo cat result.txt)
test=80
if [ $test -gt $res ]
then
		echo "yes"
else
        echo "no"
fi
    
    
------------------------
mlproject3_autobot
------------------------

if sudo docker ps -l | grep my-docker-automl
then
	echo "my-docker-automl already build"
else
	echo "my-docker-automl not build"  
fi

sudo docker run -p 5000:5000 my-docker-nn python3 train-nn.py > nn_result.txt
res=$(sudo cat nn_result.txt)
test=80

if [ "$test" -gt "$res" ]
then
		echo "accuracy not supperior to 80%"
        sudo cat nn_result.txt
else   
	   sudo docker run -p 5000:5000 my-docker-nn python3 train-auto-nn.py > auto_result.txt
	   sudo cat auto_result.txt
fi
    

=====================================================================================================

    1  sudo yum update -y
    2  sudo yum upgrade -y
    3  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
    4  sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
    5  sudo yum upgrade -y
    6  sudo amazon-linux-extras install java-openjdk11 -y
    7  sudo yum install jenkins -y
    8  sudo systemctl enable jenkins
    9  sudo systemctl start jenkins
    10  sudo systemctl status jenkins
    11  jenkins --version
    12  sudo yum install git
    13  java --version; jenkins --version; git --version
    14  sudo amazon-linux-extras | grep docker
    15  sudo amazon-linux-extras
    16  sudo amazon-linux-extras install docker
    17  docker --version
    18  sudo systemctl daemon-reload
    19  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    20  which git
    21  sudo visudo -f /etc/sudoers.d/filename   (jenkins ALL=(ALL) NOPASSWD: ALL)
    22  pwd
    23  ll
    24  ls
    25  sudo systemctl status docker
    26  sudo systemctl start docker
    27  sudo systemctl status docker
    28  sudo docker image list
    29  docker ps
    30  sudo docker ps
    31  ll
    32  git pull https://github.com/xaviervasques/Jenkins
    33  git pull https://github.com/xaviervasques/Jenkins.git
    34  git remote add origin https://github.com/xaviervasques/Jenkins.git
    35  git init
    36  git status
    37  git add .
    38  git status
    39  git remote add origin
    40  git remote add origin https://github.com/xaviervasques/Jenkins.git
    41  echo "# Jenkins" >> README.md
    42  git init
    43  git add README.md
    44  git commit -m "first commit"
    45  git branch -M main
    46  git remote add origin https://github.com/vipulwarthe/Jenkins.git
    47  git push -u origin main
    48  git remote -v
    49  git remote remove https://github.com/xaviervasques/Jenkins.git
    50  git remote remove origin https://github.com/xaviervasques/Jenkins.git
    51  git remote remove https://github.com/xaviervasques/Jenkins.git
    52  echo "# Jenkins" >> README.md
    53  git init
    54  git add README.md
    55  git commit -m "first commit"
    56  git config --global --edit
    57  git branch -M main
    58  git remote add origin https://github.com/vipulwarthe/Jenkins.git
    59  git remote -v
    60  git remote remove origin
    61  git remote -v
    62  git remote add origin https://github.com/vipulwarthe/Jenkins.git
    63  git push -u origin main
    64  git remote -v
    65  git clone https://github.com/xaviervasques/Jenkins.git
    66  ls
    67  git status
    68  git pull origin main
    69  git status
    70  git add .
    71  git status
    72  git commit -m "my second commit"
    73  git push -u origin main
    74  pwd
    75  sudo systemctl status docker
    76  sudo systemctl start docker
    77  sudo systemctl status docker
    78  sudo docker image list
    79  sudo docker ps
    80  vi Dockerfile
    81  sudo docker build -t my-docker-lda -f Dockerfile .
    82  sudo docker ps
    83  sudo docker image list
    84  sudo docker build -t my-docker-automl -f Dockerfile .
    85  sudo docker build -t my-docker-nn -f Dockerfile .
    86  sudo docker image list
    87  sudo docker ps -a
   
