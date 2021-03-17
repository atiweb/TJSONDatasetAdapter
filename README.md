# TJSONDatasetAdapter-
Encode JSON to a FireDAC Memory Table without REST Request


Credits to:

https://chapmanworld.com/2017/07/07/encode-json-to-a-firedac-memory-table-without-rest-request/
https://github.com/chapmanworld

So how do I use it?

Having installed the component, it should appear on your component palette under the “REST Client” category.
Here are some instructions for building a sample application for it:

Create a new application (VCL or FMX).
(note, you may need to set your project path to include the location of jsonadapter.pas if you did not configure this during installation).
Drop a TFDMemTable onto your form.
Drop a TJSONDatasetAdapter adapter onto your form
Drop a TStringGrid onto your form.
Set the JSONDatasetAdapter1.Dataset property to FDMemTable1
Set the JSONDatasetAdapter1.JSON property to some JSON data (see example data below).
Use live bindings to bind your FDMemTable1 component to the string grid.



Repo created after fix somes issues in the original code:
That was:
line 79:
Original: e: TJSONPairEnumerator;
Changed to:  e: TJsonObject.TEnumerator;

JSON Null types rise error:
Line 134
Original: end else if v is TJSONNull then begin
          //- Do nothing, another record may indicate data type.
          
Changed: end else if v is TJSONNull then begin
          //- Do nothing, another record may indicate data type.
          if (FieldDef.DataType=TFieldType.ftUnknown) then begin
            FieldDef.DataType := TFieldType.ftString;
          end;
          
 And that it, works perfect.
          
          
          
          
          
          
          
          
          
