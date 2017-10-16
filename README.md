# hello-world
Hello Fio!
libname test '\\client\c$\users\mhess15\desktop'; 
proc import 
	datafile= '\\client\c$\users\mhess15\Desktop\workbook2' 
	DBMS= xls
	REPLACE
	Out=test.raw1;
	GETNAMES =yes;
	run;
  
data test;
 set test.raw1;
 min=999999;
array x{*} fludate: ;
do i=1 to dim(x);
if x{i} lt min  and x{i} ne 0 then min=x{i};
end;
format min ddmmyy10.;
drop i;
run;
