# Crystal-Reports-11.5-with-PHP-and-MySQL
Crystal Reports 11.5 with PHP and MySQL
17

I am new to Crystal Reports, and I am using version Crystal Reports 11.5.

This is what I have so far:

$my_report = "E:\\xampp\\htdocs\\crystal\\Test1.rpt"; 

$my_pdf = "E:\\xampp\\htdocs\\crystal\\test.pdf"; 

$o_CrObjectFactory = new COM('CrystalReports11.ObjectFactory.1');

// Create the Crystal Reports Runtime Application.


$o_CrApplication =$o_CrObjectFactory->CreateObject("CrystalDesignRunTime.Application"); 

//------ Open your rpt file ------ 

$creport = $o_CrApplication->OpenReport($my_report, 1); 

//------ Connect to DB2 DataBase ------ 

**this is the hard part where I am not able to complete connection to mysql**
$o_CrApplication->LogOnServer('which library','mlims','root',''); 

//------ Put the values that you want -------- 

$creport->RecordSelectionFormula="{parameter.id}='1'"; 

//------ This is very important. DiscardSavedData make a 

// Refresh in your data -------

$creport->DiscardSavedData; 

//------ Read the records :-P ------- 

$creport->ReadRecords(); 

//------ Export to PDF ------- 

$creport->ExportOptions->DiskFileName=$my_pdf; 
$creport->ExportOptions->FormatType=31; 
$creport->ExportOptions->DestinationType=1; 
$creport->Export(false); 

//------ Release the variables 
$creport = null; 
$crapp = null; 
$ObjectFactory = null; 
