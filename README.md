# ec2-hadoop-scripts
Some bash scripts to automate MapReduce Hadoop setup on Amazon EC2 instances.

# How to Use
1. Create more than 2 Amazon EC2 instances, make sure that they are in the same private subnet.
2. Click "Download ZIP" button on the right and unzip it.
3. Copy the key pair generated by Amazon EC2 to ec2-hadoop-scripts-master/files/ec2.pem
3. Run `scp -i ec2-hadoop-scripts-master/files/ec2.pem -r ec2-hadoop-scripts <public ip of master instance>:~/` in a local terminal.
4. SSH into master instance and run
<br/><br/><pre><code>sudo su
cd ~/
cp -r ~ubuntu/ec2-hadoop-scripts-master ./
rm -r ~ubuntu/ec2-hadoop-scripts-master
cd ec2-hadoop-scripts-master/scripts
./master.sh</code></pre>
5. Follow the instructions on screen.
6. To setup slave instances, SSH into master instance and run (an example of private hostname is `ip-172-31-2-167`)
<br/><br/><pre><code>sudo su
cd ~/ec2-hadoop-scripts-master/scripts
./slave.sh &lt;private hostname of slave instance&gt;</code></pre>
7. Follow the instructions on screen.
8. To check the installation, first make sure that DFS and YARN are started, then browse `http://<ip of master instance>:8088/` to check results.
