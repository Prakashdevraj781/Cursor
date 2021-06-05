--Refrence Cursor

set Serveroutput On;
Declare
 Type ref_cur_type IS REF CURSOR;-- DEFINING REF CURSOR TYPE
 refvar ref_cur_type;-- REFERENCE CURSOR VARIABLE
 C1 T_LIPO_POLICY%ROWTYPE;-- VARIABLE OF LIPO RECORD TYPE
 C2 T_Litt_Transaction_Type_Code%ROWTYPE;
Begin
OPEN refvar FOR select * from t_lipo_policy where po_pln_code ='723';
LOOP
FETCH refvar into C1;
exit when refvar%NOTFOUND;
 Dbms_Output.Put_Line(C1.Po_Cont ||' ' ||C1.Po_Status);
END LOOP;
close refvar;
OPEN refvar FOR select * from T_Litt_Transaction_Type_Code;
LOOP
FETCH refvar into C2;
exit when refvar%NOTFOUND;
 Dbms_Output.Put_Line(C2.TT_TXN_TYPE_DESC ||' ' ||C2.TT_TXN_TYPE);
END LOOP;
close refvar;
End;

