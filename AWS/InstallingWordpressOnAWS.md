**Installing Wordpress on AWS**

**Part 1: Create an EC2 Instance**

-   Create your free account on AWS –
    [*http://aws.amazon.com/free*](http://aws.amazon.com/free)

-   Create an EC2 Instance.

    A.  From the AWS Management Console click on EC2.

    B.  Click on "Launch Instance" and select Quick Launch Wizard.\
        (Enter the Instance name, create a new key pair, download the
        key pair and select Ubuntu Server 12.04 or alike)

    C.  Select Amazon Linux AMI.\
        (Under Instance Details make sure **t2.micro** is selected it’s
        part of the free trial, then select Launch)

    D.  Your instance is being created.

    E.  Add rules to the Default Security Group to allow inbound access
        to EC2.\
        (port 22 = ssh and port 80 = http)

    F.  Assign an IP address by selecting Elastic IP’s.

    G.  Right click on the IP address and select Associate. Assign it to
        your new instance.

    H.  Select your new Instance and right click on it.\
        (this contains some very useful information you might need
        later on)

**Part 2: Configure your EC2 Instance**

> Now that the EC2 instance has been created it’s time to install the
> LAMP (Linux, Apache, MySQL and PHP) stack which we’ll need before you
> can install WordPress. The Linux kernel was preinstalled when the EC2
> instance was created. Apache and PHP will be installed in this
> section. MySQL will be installed in the next section.

A.  Connect to the EC2 instance.\
    There are two ways you can connect to EC2, one is to right click on
    the EC2 instance name and launch a Java SSH client. The other way is
    to use a command line SSH client. This tutorial will use Terminal.

B.  Install Apache and PHP.\
    From Terminal go to the directory(e.g. downloads) that contains
    &lt;filename&gt;.pem (the file contains your credentials to access
    your EC2 instance.)

> Change the permission of the file:
>
> **chmod 400 \[filename\].pem**
>
> Connect to your EC2 instance:
>
> **ssh -i \[filename\].pem ubuntu@\[Elastic IP\]**
>
> Switch to superuser:
>
> **sudo su**
>
> Install any new updates:
>
> **sudo apt-get update**
>
> Install Apache:
>
> **apt-get -y install apache2**
>
> Install PHP:
>
> **apt-get -y install php5 php5-mysql**

**Part 3: Create an RDS Instance**

A.  From the Management Console click on RDS and then select Launch a
    DB Instance.

B.  Select MySQL Community Edition.

C.  Step 3: Select **db.t2.micro**, no for Multi-AZ.\
    (db.t2.micro is part of the Free Trial. But if it does not work, you
    may select something different.) Remember the Master Username and
    Master Password for WordPress.

D.  Enter a Database Name.\
    (Remember the Database Name for WordPress)

E.  Select the defaults.

F.  Select Launch DB Instance.

G.  The database may take 5 minutes to create.

H.  Click on DB Security Groups (left-side panel menu) and click on the
    magnifying glass.

I.  Verify the EC2 Security Group is authorized

J.  Click on Instance and review the information for the DB you created\
    (Remember the Endpoint for WordPress)

**Part 4: Install WordPress**

A.  Download and install WordPress.

> From Terminal go to the directory that contains &lt;filename&gt;.pem
>
> Change the permission of the file:
>
> **chmod 400 \[filename\].pem**
>
> Connect to your EC2 instance:
>
> **ssh -i \[filename\].pem ubuntu@\[Elastic IP\]**
>
> Switch to superuser:
>
> **sudo su**
>
> Change to the root directory:
>
> **cd /var/www**
>
> Download the latest WordPress package:
>
> **wget http://wordpress.org/latest.tar.gz**
>
> Extract WordPress:
>
> **tar -xzvf latest.tar.gz**
>
> Move WordPress to the root www folder:
>
> **mv wordpress/\* /var/www/html/**
>
> Delete the WordPress tar file and the existing index.html file
>
> **rm latest.tar.gz**
>
> **rm index.html**
>
> Change permissions on the directory:
>
> **chown -hR www-data:www-data /var/www**
>
> **chmod -R g+rw /var/www**
>
> Restart the Apache server
>
> **service apache2 restart**

A.  Point your browser to the Elastic IP address and create the config
    file (wp-config.php)\
    (RDS Endpoint without the ":3306" - Go to the RDS to get
    this endpoint.)

B.  Enter the configuration details and submit.

C.  Finish the installation of WordPress.

D.  Go to your Elastic IP address and visit your new blog – Hello World!

**Part 5: Configure S3**

> S3 will be used to serve up media images (jpg, png, etc...) on the
> WordPress blog. S3 uses the term “bucket”, think of it as a container
> for your files. The bucket name has to be unique across the entire S3
> platform.

A.  From the Management Console click on S3 and select Create Bucket.

B.  Enter a bucket name.

C.  Click on Upload and add an image.\
    (Use the S3 link when adding an image to a blog post in WordPress)

> **You may install S3 Browser – Window Client for Amazon S3 and Amazon
> Cloud Front**
