<?php
session_start();
error_reporting(0);
//trying to show changes
?>
<!DOCTYPE html>
<html lang="en">
	<head>
		<title>Admin | View Students</title>
		<a href="home.php">Home ..</a>
		
		<link href="http://fonts.googleapis.com/css?family=Lato:300,400,400italic,600,700|Raleway:300,400,500,600,700|Crete+Round:400italic" rel="stylesheet" type="text/css" />
		<link rel="stylesheet" href="vendor/bootstrap/css/bootstrap.min.css">
		<link rel="stylesheet" href="vendor/fontawesome/css/font-awesome.min.css">
		<link rel="stylesheet" href="vendor/themify-icons/themify-icons.min.css">
		<link href="vendor/animate.css/animate.min.css" rel="stylesheet" media="screen">
		<link href="vendor/perfect-scrollbar/perfect-scrollbar.min.css" rel="stylesheet" media="screen">
		<link href="vendor/switchery/switchery.min.css" rel="stylesheet" media="screen">
		<link href="vendor/bootstrap-touchspin/jquery.bootstrap-touchspin.min.css" rel="stylesheet" media="screen">
		<link href="vendor/select2/select2.min.css" rel="stylesheet" media="screen">
		<link href="vendor/bootstrap-datepicker/bootstrap-datepicker3.standalone.min.css" rel="stylesheet" media="screen">
		<link href="vendor/bootstrap-timepicker/bootstrap-timepicker.min.css" rel="stylesheet" media="screen">
		<link rel="stylesheet" href="assets/css/styles.css">
		<link rel="stylesheet" href="assets/css/plugins.css">
		<link rel="stylesheet" href="assets/css/themes/theme-1.css" id="skin_color" />
	</head>
	<body>
		<div id="app">		
<div class="app-content">
<?php include('include/headers.php');?>
<div class="main-content" >
<div class="wrap-content container" id="container">
						<!-- start: PAGE TITLE -->
<section id="page-title">
<div class="row">
<div class="col-sm-8">
<h1 class="mainTitle">Admin | View Students</h1>
</div>
<ol class="breadcrumb">
<li>
<span>Admin</span>
</li>
<li class="active">
<span>View Students</span>
</li>
</ol>
</div>
</section>
<div class="container-fluid container-fullw bg-white">
<div class="row">
<div class="col-md-12">
<h4 class="tittle-w3-agileits mb-4"></h4>
<?php

$studentid=$_POST['studentid'];
$studentname=$_POST['studentname'];
$age=$_POST['age'];
$gender=$_POST['gender'];
$unitcode=$_POST['unitcode'];

?>
<form role="form" method="post" name="search">

<div class="form-group">
<label for="">
Search by Name/Student id.
</label>
<input type="text" name="searchdata" id="searchdata" class="form-control" value="" required='true'>
</div>

<button type="submit" name="search" id="submit" class="btn btn-o btn-success ">
Search
</button>
</form>
<!--<h5 align="center" style="color:blue">Report By age <?php echo $fdate?> to <?php echo $tdate?></h5>-->
	
<table class="table table-hover" id="sample-table-1">
<thead>
<tr>
<th class="center">#</th>
<th>Student Id</th>
<th>Student Name</th>
<th>Student Gender </th>
<th>Unitname  </th>
</tr>
</thead>
<tbody>
<?php
include 'connection.php';
if (isset($_POST['search'])) {
	$sdata=$_POST['searchdata'];

	 //$query=mysqli_query($conn,"SELECT * from students where studentid like '%$sdata%'");
$query="SELECT * from students where  studentname like '%$sdata%' || studentid like '%$sdata%'";

$num=count($query);
//$num=mysqli_num_rows($query);

if($num>0){
$cnt=1;
 $data = mysqli_query($conn, $query);


   if (!$data) {
       echo("Error description: " . mysqli_error($mysqli));
   } else {

       while ($row = mysqli_fetch_array($data)) 
	   {
		  
 ?>
		   <tr>
				<td><?php echo $cnt;?>.</td>
       			<td><?php echo $row['studentid'];?></td>
				<td class="hidden-xs"><?php echo $row['studentname'];?></td>
				<td class="hidden-xs"><?php echo $row['gender'];?></td>
				<td class="hidden-xs"><?php echo $row['unitcode'];?></td>
            </tr>
		<?php	
		$cnt=$cnt+1;
       }
   }
}

}?></tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
			<!-- start: FOOTER -->
				
			<!-- end: SETTINGS -->
		</div>
		<!-- start: MAIN JAVASCRIPTS -->
		<script src="vendor/jquery/jquery.min.js"></script>
		<script src="vendor/bootstrap/js/bootstrap.min.js"></script>
		<script src="vendor/modernizr/modernizr.js"></script>
		<script src="vendor/jquery-cookie/jquery.cookie.js"></script>
		<script src="vendor/perfect-scrollbar/perfect-scrollbar.min.js"></script>
		<script src="vendor/switchery/switchery.min.js"></script>
		<!-- end: MAIN JAVASCRIPTS -->
		<!-- start: JAVASCRIPTS REQUIRED FOR THIS PAGE ONLY -->
		<script src="vendor/maskedinput/jquery.maskedinput.min.js"></script>
		<script src="vendor/bootstrap-touchspin/jquery.bootstrap-touchspin.min.js"></script>
		<script src="vendor/autosize/autosize.min.js"></script>
		<script src="vendor/selectFx/classie.js"></script>
		<script src="vendor/selectFx/selectFx.js"></script>
		<script src="vendor/select2/select2.min.js"></script>
		<script src="vendor/bootstrap-datepicker/bootstrap-datepicker.min.js"></script>
		<script src="vendor/bootstrap-timepicker/bootstrap-timepicker.min.js"></script>
		<!-- end: JAVASCRIPTS REQUIRED FOR THIS PAGE ONLY -->
		<!-- start: CLIP-TWO JAVASCRIPTS -->
		<script src="assets/js/main.js"></script>
		<!-- start: JavaScript Event Handlers for this page -->
		<script src="assets/js/form-elements.js"></script>
		<script>
			jQuery(document).ready(function() {
				Main.init();
				FormElements.init();
			});
		</script>
		<!-- end: JavaScript Event Handlers for this page -->
		<!-- end: CLIP-TWO JAVASCRIPTS -->
		//removed first change line...
//new line testing
	</body>
</html>
