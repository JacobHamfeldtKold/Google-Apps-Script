# Google-Apps-Script

Put a command like this in the top left cell of all sheets in the same spreadsheet to import sheets into the same spreadsheet. The "select * WHERE Col1 is not Null "    part is nescescary to prevent the GAS command getDataRange from not selecting all the empty cells that would otherwise come from the importet sheet.    

=QUERY(IMPORTRANGE("1lkXFdivuMynkpqOlP6ZtFPNbgpfbspxyP5mYQccGKJY", "ark1!A:M"),"select * WHERE Col1 is not Null ", 1)


Then in tools => scripteditor use this as a template. Then put in your own spreadsheet ID's and sheetnames.






function sammensætalleområder() {
    
    // Sletter alt data i arket "Data alle uddannelser" og sætter alt data fra de andre uddannelser ind i samme ark"

  var sheet_kombiner_alle = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("Alle områder kombineret"); 
  sheet_kombiner_alle.clear(); // Sletter alt gammel data. 
  var first_empty_row = 1;
  
    
  var sheet_EVU = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("EVU");
  var EVU_data_range = sheet_EVU.getDataRange();
  var coming_last_row = EVU_data_range.getLastRow() + first_empty_row;
  EVU_data_range.copyValuesToRange(789128935, 1, 16, first_empty_row, coming_last_row);
  first_empty_row = EVU_data_range.getLastRow() + first_empty_row;
  
  
  var sheet_NYK_GU = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("NYK GU");
  var NYK_GU_data_range = sheet_NYK_GU.getDataRange();
  coming_last_row = first_empty_row + NYK_GU_data_range.getLastRow() + 1 ;
  NYK_GU_data_range.copyValuesToRange(789128935, 1, 16, first_empty_row, coming_last_row );
  sheet_kombiner_alle.deleteRow(first_empty_row);
  first_empty_row = NYK_GU_data_range.getLastRow() + first_empty_row -1; // The -1 here is because the header is deleted on the above line.
  
  
  var sheet_FoU = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("FoU");
  var FoU_data_range = sheet_FoU.getDataRange();
  coming_last_row = first_empty_row + FoU_data_range.getLastRow() + 1 ;
  FoU_data_range.copyValuesToRange(789128935, 1, 16, first_empty_row, coming_last_row );
  sheet_kombiner_alle.deleteRow(first_empty_row);
  first_empty_row = FoU_data_range.getLastRow() + first_empty_row -1; // The -1 here is because the header is deleted on the above line.
  
  
  var sheet_VOR_GU = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("VOR GU");
  var VOR_GU_data_range = sheet_VOR_GU.getDataRange();
  coming_last_row = first_empty_row + VOR_GU_data_range.getLastRow() + 1 ;
  VOR_GU_data_range.copyValuesToRange(789128935, 1, 16, first_empty_row, coming_last_row );
  sheet_kombiner_alle.deleteRow(first_empty_row);
  first_empty_row = VOR_GU_data_range.getLastRow() + first_empty_row -1; // The -1 here is because the header is deleted on the above line.
  
  
  var sheet_SLA_GU = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("SLA GU");
  var SLA_GU_data_range = sheet_SLA_GU.getDataRange();
  coming_last_row = first_empty_row + SLA_GU_data_range.getLastRow() + 1 ;
  SLA_GU_data_range.copyValuesToRange(789128935, 1, 16, first_empty_row, coming_last_row );
  sheet_kombiner_alle.deleteRow(first_empty_row);
  first_empty_row = SLA_GU_data_range.getLastRow() + first_empty_row -1; // The -1 here is because the header is deleted on the above line.
  
  
  var sheet_ROS_GU = SpreadsheetApp.openById("1kEHtk3lcSwJaNLfkt9FazxUQJIe5T5SPvUdlVQpHzkM").getSheetByName("ROS GU");
  var ROS_GU_data_range = sheet_ROS_GU.getDataRange();
  coming_last_row = first_empty_row + ROS_GU_data_range.getLastRow() + 1 ;
  ROS_GU_data_range.copyValuesToRange(789128935, 1, 16, first_empty_row, coming_last_row );
  sheet_kombiner_alle.deleteRow(first_empty_row);
  first_empty_row = ROS_GU_data_range.getLastRow() + first_empty_row -1; // This line is unnescecary but included to create symmetry. 
  
}
