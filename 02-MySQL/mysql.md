# MySQL

1. Install mysql-apt.deb
    
    In https://dev.mysql.com/downloads/repo/apt/ , click **Download**.

    After downloading, in the new opening **mysql-apt-config** window, click **install**.

    >The downloaded .deb will override the default one in package managers. We recommand to use the downloaded one which is community editon.

2. Install MySQL.

        sudo apt install mysql-server

3. Check the status of MySQL. Usually its state is active and running.

        sudo systemctl status mysql 

4. Access MySQL. 

        sudo mysql

    To exit MySQL, type `exit;`