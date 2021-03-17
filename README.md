# TJSONDatasetAdapter
Encode JSON to a FireDAC Memory Table without REST Request


Credits to:<br>
https://chapmanworld.com/2017/07/07/encode-json-to-a-firedac-memory-table-without-rest-request/ <br>
https://github.com/chapmanworld
<br><br>
So how do I use it?<br>

Having installed the component, it should appear on your component palette under the “REST Client” category.<br>
Here are some instructions for building a sample application for it:<br><br>

Create a new application (VCL or FMX).<br>
(note, you may need to set your project path to include the location of jsonadapter.pas if you did not configure this during installation).<br>
Drop a TFDMemTable onto your form.<br>
Drop a TJSONDatasetAdapter adapter onto your form<br>
Drop a TStringGrid onto your form.<br>
Set the JSONDatasetAdapter1.Dataset property to FDMemTable1<br>
Set the JSONDatasetAdapter1.JSON property to some JSON data (see example data below).<br>
Use live bindings to bind your FDMemTable1 component to the string grid.<br>

<br><br><br>

Repo created after fix somes issues in the original code:<br>
That was:<br>
line 79:<br>
Original: e: TJSONPairEnumerator;<br>
Changed to:  e: TJsonObject.TEnumerator;<br>
<br>
JSON Null types rise error:<br>
Line 134<br>
Original: end else if v is TJSONNull then begin<br>
          //- Do nothing, another record may indicate data type.<br><br>
          
Changed: end else if v is TJSONNull then begin<br>
          //- Do nothing, another record may indicate data type.<br>
          if (FieldDef.DataType=TFieldType.ftUnknown) then begin<br>
            FieldDef.DataType := TFieldType.ftString;<br>
          end;<br>
          <br>
 And that it, works perfect.<br>
          
          
          
 # A more robust solution can be found in:
 https://github.com/danieleteti/delphimvcframework/blob/master/sources/MVCFramework.DataSet.Utils.pas <br>
 <br>
 as part of te DMVCFramework by Daniele Teti:<br>
 https://github.com/danieleteti/delphimvcframework
          
          
          
          
          
