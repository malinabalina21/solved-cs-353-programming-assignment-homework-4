Download Link: https://assignmentchef.com/product/solved-cs-353-programming-assignment-homework-4
<br>
In this assignment, you will first write a simple Java application to connect to a MySQL database and modify it. Next, you are required to design a basic internet application using PHP on top of this database. In what follows, we explain each of these stages in detail.

<strong>Part 1: Connecting to the database with a Java application </strong>

For this part of the assignment, you will first connect to your database using MySQL console, and then write a simple Java application to connect and interact with this database.

 <em>Connecting to the database</em>: Connect to the dijkstra.ug.bcc.bilkent.edu.tr machine, which runs MySQL server (Use <strong>SSH</strong> or PUTTY as dijkstra allows only “secure” shell connections but not telnet!). Next, in the shell prompt, execute the command

shell&gt; mysql –user=USERNAME –pass=PASSWORD;

To connect to the dijkstra server and MySQL, you need a username and password, which should be e-mailed to you by now.  This MySQL account should contain a database whose name is the same as your username. For instance, if your username is “ahmetc” then you should have a database with the name ahmetc. Check your databases with ‘show databases;’ command in mysql. For the user “ahmetc” the output is as follows:

mysql&gt; show databases;

+——————–


| Database           |

+——————–


| information_schema |

| ahmetc           |

| test               |

+——————–





If you don’t have a database named as your username create it with the command:

‘create database your_user_name;’ (create database ahmetc; for the above example) Contact to the TA immediately, if you encounter any problem connecting to your database.

Next, write a Java program that does the following:




<ul>

 <li><em>Connection</em>: Successfully connect to your MySQL database using Java and your MySQL account information. You can easily find the JDBC driver for MySQL on the Web.</li>

</ul>




<ul>

 <li><em>Table creation:</em> Create the following relations in your database. <strong>REMARK:</strong> We want to set the foreign key relationships, and in MySQL this is supported with <strong><u>InnoDB</u></strong> Do NOT forget to set table type to InnoDB and set foreign keys for each table appropriately. (Again, see MySQL reference manual for details).</li>

</ul>

<strong> </strong>

<strong>student</strong><u>(<em>sid</em>: CHAR(12),</u> s<em>name</em>: VARCHAR(50), <em>bdate</em>: DATE, <em>telno</em>: CHAR(10), <em>scity</em>: VARCHAR(20), <em>year</em>: CHAR(20), <em>gpa</em>: FLOAT)




<strong>company</strong>(<em><u>cid</u></em><u>: CHAR(8)</u>, <em>cname</em>: VARCHAR(20), <em>quota</em>: INT)




<strong>apply</strong>(<em><u>sid</u></em><u>: CHAR(12), <em>cid</em>: CHAR(8)</u>)




<ul>

 <li><em>Table population:</em> Insert into the newly created relations the following records.</li>

</ul>




<table width="400">

 <tbody>

  <tr>

   <td colspan="7" width="400"><strong>student</strong></td>

  </tr>

  <tr>

   <td width="63"><strong>Sid</strong></td>

   <td width="46"><strong>sname</strong></td>

   <td width="71"><strong>bdate</strong></td>

   <td width="78"><strong>telno</strong></td>

   <td width="53"><strong>scity</strong></td>

   <td width="60"><strong>year</strong></td>

   <td width="30"><strong>gpa</strong></td>

  </tr>

  <tr>

   <td width="63">21000001</td>

   <td width="46">Ayse</td>

   <td width="71">10.05.1995</td>

   <td width="78">5321113333</td>

   <td width="53">Ankara</td>

   <td width="60">senior</td>

   <td width="30">2,75</td>

  </tr>

  <tr>

   <td width="63">21000002</td>

   <td width="46">Ali</td>

   <td width="71">12.09.1997</td>

   <td width="78">5355361234</td>

   <td width="53">Istanbul</td>

   <td width="60">junior</td>

   <td width="30">3,44</td>

  </tr>

  <tr>

   <td width="63">21000003</td>

   <td width="46">Veli</td>

   <td width="71">25.10.1998</td>

   <td width="78">5553214455</td>

   <td width="53">Istanbul</td>

   <td width="60">freshman</td>

   <td width="30">2,36</td>

  </tr>

  <tr>

   <td width="63">21000004</td>

   <td width="46">John</td>

   <td width="71">15.01.1999</td>

   <td width="78">5335336622</td>

   <td width="53">Chicago</td>

   <td width="60">freshman</td>

   <td width="30">2,55</td>

  </tr>

 </tbody>

</table>




<table width="386">

 <tbody>

  <tr>

   <td colspan="3" width="204">               <strong>company</strong>                  <strong> </strong></td>

   <td rowspan="12" width="39"> </td>

   <td colspan="2" width="143"><strong>apply</strong></td>

   <td width="0"></td>

  </tr>

  <tr>

   <td width="39"><strong>cid </strong></td>

   <td width="112"><strong>cname </strong></td>

   <td width="53"><strong>quota </strong></td>

   <td width="63"><strong>sid </strong></td>

   <td width="80"><strong>cid </strong></td>

   <td width="0"></td>

  </tr>

  <tr>

   <td width="39">C101</td>

   <td width="112">tubitak</td>

   <td width="53">2</td>

   <td width="63">21000001</td>

   <td width="80">C101</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td width="39">C102</td>

   <td width="112">aselsan</td>

   <td width="53">5</td>

   <td width="63">21000001</td>

   <td width="80">C102</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td rowspan="2" width="39">C103</td>

   <td rowspan="2" width="112">havelsan</td>

   <td rowspan="2" width="53">3</td>

   <td width="63">21000001</td>

   <td width="80">C103</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td rowspan="2" width="63">21000002</td>

   <td rowspan="2" width="80">C101</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td rowspan="2" width="39">C104</td>

   <td rowspan="2" width="112">microsoft</td>

   <td rowspan="2" width="53">5</td>

  </tr>

  <tr>

   <td rowspan="2" width="63">21000002</td>

   <td rowspan="2" width="80">C105</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td rowspan="2" width="39">C105</td>

   <td rowspan="2" width="112">merkez bankasi</td>

   <td rowspan="2" width="53">3</td>

  </tr>

  <tr>

   <td width="63">21000003</td>

   <td width="80">C104</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td width="39">C106</td>

   <td width="112">tai</td>

   <td width="53">4</td>

   <td width="63">21000003</td>

   <td width="80">C105</td>

   <td width="0"></td>

  </tr>

  <tr>

   <td width="39">C107</td>

   <td width="112">milsoft</td>

   <td width="53">2</td>

   <td width="63">21000004</td>

   <td width="80">C107</td>

   <td width="0"></td>

  </tr>

 </tbody>

</table>




<ul>

 <li>Execute the command “SELECT * FROM student” and print the results on screen.</li>

</ul>




<ul>

 <li>While doing the above tasks, give meaningful error messages when necessary. For instance, login information (e.g., password) may be wrong, etc.).</li>

</ul>




<ul>

 <li>Recall that your program may be executed several times during your code development and during the grading. So, you should check whether the database and/or tables actually exist before trying to create them to prevent MySQL errors. If they exist, first drop them and then re-create them.</li>

</ul>

<strong> </strong>

<strong>Part 2: A simple Web based application using PHP </strong>




For this part of the assignment, you are required to design an internet application on top of the internship database you created above. In particular, you will design and implement a website that involves the middle and presentation tiers of a web application and makes use of the internship database at the data management tier. The website should include the following pages:




<ol>

 <li><em>Index page:</em> All users start at a common log on page, where each user is expected to enter his/her login and password. We assume that student names serve as logins and student id’s serve as passwords (for instance, student “Ayse” can login by entering “ayse” and “21000001” as her login and password). Note that, login is case-insensitive. Give an appropriate error message if the log-on operation fails. In addition, give an error if one or both of the input fields left blank and “login” button is clicked (i.e., use a simple Java Script code to check).</li>

</ol>




<ol start="2">

 <li><em>Student welcome page:</em> In this homework, we consider a summer internship application system. In the welcome page which shows all the companies (cid, cname and quota fields) in which student has applied for internships. Students can apply <strong>up to 3 </strong>companies<strong>.</strong> Next to each of these internship applications, display a link, namely “Cancel”, so that the student can cancel this application. When the student clicks on the “Cancel” link, display either an “error message” or a “successful deletion” message, and allow the student to return to student welcome page, again (which, of course, doesn’t display the tuple(s) deleted from the apply table).</li>

</ol>

At the bottom of this page, also provide a link called “apply for new internship”. If student has already applied for 3 companies, give an appropriate error message (either at a new page or a dialog box) when (s)he clicks on this link. Otherwise, when this link is clicked, open a new page.




At this page, show ids and names of those <em>candidate</em> companies that are not applied by this particular student (You should not show the company if all of its internship quota is filled.). Also provide an input field and a “submit” button, so that the student can choose to apply in one of these displayed companies (e.g., by typing the company id and clicking on the submit button). Again, show an appropriate message after the addition and allow user to return to the previous page. At every page, remember to put a link to an appropriate previous page, so that the student can go back without doing any modifications. Also, you may need to keep track of the current student id through pages, as well.




Finally, a logout link in all appropriate pages will be useful.




<strong>IMPLEMENTATION</strong> You should use PHP to implement the application logic (except the Java Script codes used to check blank form fields at the client side). Your application should connect to your MySQL database prepared in the first part of this assignment.




Test your web pages under your public html directory (at <em>dijkstra</em>) in a folder called <em>surname_name</em> (if the public_html directory does not exist, create it at your home directory and set its r-w-x permissions appropriately). You will copy and submit this folder as described below, and we will copy it under our own public_html and execute there. To allow this, please use <em>relative links</em> in your web pages (i.e., if you include links to an absolute page like http:// …/~ahmet/can_ahmet /index.php, it would not work under our public html folder. If this happens<strong>, you won’t get any grade</strong> from this part of the assignment).




<strong>What to submit? </strong>

<strong> </strong>

You will submit a WinRAR file including two folders, part1 and part2. Folders must be <strong><u>exactly</u></strong> named as <em>surname_name_p1</em> and <em>surname_name_p2 (please do not use Turkish characters)</em>. The RAR file must be named as <em>surname_name.</em> Each folder should include the following:




<ul>

 <li>part1 folder: In this folder, provide the Java source code file(s).</li>

 <li>part2 folder: This folder should include all your PHP files. We will copy them to our public_html and then execute there.</li>

</ul>




For both parts, grading will be based on the <strong>execution</strong> of your code.




<strong>Where to submit? </strong>




You will use the Moodle course page for submission of this assignment. If you encounter a problem during submission, please send your assignment by email to your TAs.


