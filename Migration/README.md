# Migration Code

<h4>The Migration Code write to make changes in Database, This code is executed one time only when the <u>bench migrate</u> command is run</h4>
<div>
  <h3>The following steps show you how to write and add any migration code</h3>
  <ol>
    <li> Create <b>patches</b> Folder in App Folder </li>
    <li> Save the migration code file in the patches folder </li>
    <li> 
      Don't Forget to Add the Migration code file to <b>patches.txt</b> File, Like this
      <br>
      <img src="imgs/patches-file.png" />
    </li>
    <li> Run the <u>bench migrate</u> command </li>
  </ol>
  <h6> This image shows you the migration code that is used to add the data of some table to another table.</h6>
  <img src="imgs/code2.png" />
  <p><b><u>In this case,</u></b>The code will get the first name and double name data from Emp First Name Doctype then put it as a full name in the full name field in Fullname Doctype </p>
</div>
