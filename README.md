# excel_practo

Mgmt_Digit
 -----------
 =COUNTIFS(NM_Claim[coinsurance_flag],
 
                          "Digit-CL",
						  
						  NM_Claim[CR Month],
						  
						  TEXT(Mgmt_Digit!B$2,"YYYYMM"),
						  
						  NM_Claim[product_lob],
						  
						  Mgmt_Digit!$A3)
						  
						  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR QTR],Mgmt_Digit!B$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
						  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],TEXT(Mgmt_Digit!B$2,"YYYYMM),NM_Claim[product_lob],Mgmt_Digit!$A3)
						  =COUNTIFS(NM_Claim[coinsurance_flag]),"Digit-CL",NM_Claim[CR Month],TEXT(Mgmt_Digit!N$2,"YYYYMM"),NM_Claim[product_lob],Mgmt_Digit!$A3)
						  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!N$2,"YYYYMM"),NM_Claim[product_lob],Mgmt_Digit!$A3)
						  
						  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!O$2,"YYYYMM"),NM_Claim[product_lob],Mgmt_Digit!$A3)
						  
			Alternate     =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],Mgmt_Digit!B$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
			
			  QRR Cal            =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Qtr],Mgmt_Digit!F$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
			  
			  FY Cal             =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR FY],Mgmt_Digit!J$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
			                     =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR FY],Mgmt_Digit!J$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
				

				Jan-25          =TEXT(EOMONTH(Base!$B$1,-3),"MMM-YY")
  
  Quater
---------  
  =COUNTIFS(NM_Claim[coinsurance_flag],
  "Digit-CL",
  NM_Claim[CR Qtr],
  Mgmt_Digit!F$2,
  NM_Claim[product_lob],
  Mgmt_Digit!$A3)
  
  
  
  Jab-25=TEXT(EOMONTH(Base!$B$1,-3),"MMM-YY")       //Return first 3 letter of month with last 2 digit of year
  Feb-25=TEXT(EOMONTH(Base!$B$1,-2),"MMM-YY")
  March-25=TEXT(EOMONTH(Base!$B$1,-1),"MMM-YY")
  April-25=TEXT(EOMONTH(Base!$B$1),"MMM-YY")
  
  Dec-24==TEXT(EOMONTH(Base!$B$1,-4),"MMM-YY")
  Nov-24=e!$B$1,-5),"MMM-YY") etc.....
  
  
  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR QTR],Mgmt_Digit!B$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
  
  
  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Qtr],Mgmt_Digit!R$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Qtr],Mgmt_Digit!R$2,NM_Claim[prod_lob],Mgmt_Digit!A$3)-wrong
  
  =COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL FY],Mgmt_Digit!V$2,NM_Claim[product_lob],Mgmt_Digit!$A3)
  
  -------------------------------------------------------------------------
  % Calc in financial year               N3= Jan-25=Claim closed month
                                         Z2=Jan-25 Current working state     //CR=Claim Register   CL=Claim Closed
										 B3=Claim register month
										 
  
  =IFERROR(
          N3/
              (  COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
                 NM_Claim[product_lob],Mgmt_Digit!$A3,
                 NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,   // if the CR Month is less than the formatted date in Z$2 of the Mgmt_Digit sheet.
                 NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1)  //  if the CL Month is greater than or equal to the formatted date in Z$2 of the Mgmt_Digit sheet.
                                                                           //Value=16
           +
   
                COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
                NM_Claim[product_lob],Mgmt_Digit!$A3,
                NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,   // if the CR Month is less than the formatted date in Z$2 of the Mgmt_Digit sheet.
                NM_Claim[CL Month],"-")+B3),"-")                          //22      Total Sum=16+22=38
				
				
				=IFERROR(N3/
				(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
				NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1)+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
				NM_Claim[CL Month],"-")+B3),"-")
				
				check
				=IFERROR(Z3/
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AA$2,"YYYYMM")*1,
				NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!AA$2,"YYYYMM")*1)
				
				+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AA$2,"YYYYMM")*1,NM_Claim[CL Month],"-")+N3,"-")
				
				=IFERROR(
				          N3/
						  
						   (  COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
						     NM_Claim[product_lob],Mgmt_Digit!$A3,
							 NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
							 NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1)
							 +
							 COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
							 NM_Claim[product_lob],Mgmt_Digit!$A3,
							 NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
							 NM_Claim[CL Month],"-")+B3),"-")
				
				
				
				Summerize of Chunks of Syntax
				-----------------------------
				
				
   "<" & TEXT(Mgmt_Digit!Z$2, "YYYYMM") * 1

      "<": This is a text string representing the less-than operator.
      TEXT(Mgmt_Digit!Z$2, "YYYYMM"): This converts the date in cell Z2 of the Mgmt_Digit sheet to a text string in the format "YYYYMM".
     * 1: This converts the text string to a number. Multiplying by 1 is a common trick to convert text to a number in Excel.
    "<" & TEXT(Mgmt_Digit!Z$2, "YYYYMM") * 1: The & symbol concatenates the less-than operator with the numeric value of the formatted date.
	For example, if Z2 contains 2025-04-15, TEXT(Mgmt_Digit!Z$2, "YYYYMM") would produce "202504", and multiplying by 1 converts it to 202504.
   	The result of the concatenation is "<202504".
     ">=" & TEXT(Mgmt_Digit!Z$2, "YYYYMM") * 1

    ">=": This is a text string representing the greater-than-or-equal-to operator.
    TEXT(Mgmt_Digit!Z$2, "YYYYMM"): This converts the date in cell Z2 of the Mgmt_Digit sheet to a text string in the format "YYYYMM".
    * 1: This converts the text string to a number.
  ">=" & TEXT(Mgmt_Digit!Z$2, "YYYYMM") * 1: The & symbol concatenates the greater-than-or-equal-to operator with the numeric value of the formatted date. For example, if Z2 contains 2025-04-15, TEXT(Mgmt_Digit!Z$2, "YYYYMM") would produce "202504", and multiplying by 1 converts it to 202504. The result of the concatenation is ">=202504".
   Summary
    The & symbol is used to concatenate text strings and values.
   In the formula, it combines operators ("<" and ">=") with formatted date values to create criteria for the COUNTIFS function.
   This allows the COUNTIFS function to compare the CR Month and CL Month columns with the formatted date values.
				
				
				
				
	IMP Note :=
    NM_Claim[CR Month],TEXT(Mgmt_Digit!Z$2,"YYYYMM")  // Here We have take Month as reference Column wise it changes and row wise it won't change..
	Column wise month change like Jan-25,Feb-25,March-25 etc but Column wise Jan-25 Month will be same but wrt fire,WC,Engineering and misc value wise it
	is different but Jan-25 wise it will same.
	
	
	Total percentage Calculation :-
	=Z14/(
	        COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
			NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
			NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1)
			+
			COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
			NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
			NM_Claim[CL Month],"-")+N14)
		
             Check below	:- Here In final Percentage we won't take Product Lob because we already took all after that final percentage will accumulate 	
				
				=Z14/( 
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
				NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1)
				+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
				NM_Claim[CL Month],"-")+N14)
				
				
				
				
				
				==============================*********************==================================
				
				% Calculation Format :-
				
				=IFERROR(Z3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,
				NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1)+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!Z$2,"YYYYMM")*1,NM_Claim[CL Month],"-")+N3),"-")
				
				=IFERROR(AA3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AA$2,"YYYYMM")*1,NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!AA$2,"YYYYMM")*1)+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AA$2,"YYYYMM")*1,NM_Claim[CL Month],"-")+O3),"-")
				
				=IFERROR(AB3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AB$2,"YYYYMM")*1,
				NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!AB$2,"YYYYMM")*1)+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AB$2,"YYYYMM")*1,NM_Claim[CL Month],"-")+P3),"-")
				
				
				=IF(W3="Closed",TEXT(AB3,"YYYYMM")*1,"-")
				
				=COUNTIF(NM_Claim[CL Month],"-")
				
				
				=IFERROR(AC3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AC$2,"YYYYMM")*1,
				NM_Claim[CL Month],">="&TEXT(Mgmt_Digit!AC$2,"YYYYMM")*1)+
				COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Month],"<"&TEXT(Mgmt_Digit!AC$2,"YYYYMM")*1,NM_Claim[CL Month],"-")+Q3),"-")
				
				=====================================================================================================
				
				=IFERROR(R3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],">="&Mgmt_Digit!AD$2)+COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[product_lob],Mgmt_Digit!$A3,NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],"-")+F3),"-")
				
				=IFERROR(AH3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],">="&Mgmt_Digit!AD$2)+ 
				COUNTIFS(NM_Claim[coinsurnce_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],"-")+R3,"-")
				
				
				
				
				=======================================================================================
				case1
				=IFERROR(AH3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],">="&Mgmt_Digit!AD$2)+COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[product_lob],Mgmt_Digit!$A3,NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],"-")+R3),"-")
				
				
				case2
				=IFERROR(AH3/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,
				NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],">="&Mgmt_Digit!AD$2)+COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[product_lob],Mgmt_Digit!$A3,NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],"-")+R3),"-")
				
				
				=====================================================================================================================
				
				=R14/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,
				NM_Claim[CL Qtr],">="&Mgmt_Digit!AD$2)+COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
				NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],"-")+F14)
				
				
				
				
				
				
				
				=AD14/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL", NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],">="&Mgmt_Digit!AD$2)+COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Qtr],"<"&Mgmt_Digit!AD$2,NM_Claim[CL Qtr],"-")+R14
				
	==================================================================================================================================================

=IFERROR(V3/(
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,NM_Claim[CR FY],"<"&Mgmt_Digit!AH$2,
NM_Claim[CL FY],">="&Mgmt_Digit!AH$2)+COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,NM_Claim[CR FY],"<"&Mgmt_Digit!AH$2,
NM_Claim[CL FY],"-")+J3),"-")


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A3,NM_Claim[CR FY],"<"&Mgmt_Digit!AH$2,NM_Claim[CL FY],">="&Mgmt_Digit!AH$2)	


=IFERROR(AH14/(COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",
NM_Claim[CR FY],"<"&Mgmt_Digit!AH$2,NM_Claim[CL FY],">="&Mgmt_Digit!AH$2)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR FY],"<"&Mgmt_Digit!AH$2,NM_Claim[CL FY],"-")+V14),"-")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A20)


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[TAT],"<=7")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[claim_status],"OPEN",NM_Claim[TAT],"<=7")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[TAT],">14",NM_Claim[TAT],"<=30")

=COUNTIFS(NM_Claim[coinsurance_flag],NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[claim_status],"OPEN",NM_Claim[TAT],">=15",NM_Claim[TAT],"<30")



=MAXIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[sub_process],"<>Litigation")

=MAXIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[claim_status],"OPEN",NM_Claim[sub_process],"<>Litigation")



=SUMIFS(NM_Claim[provision_amt],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A20)/10^5

=SUMIFS(NM_Claim[provision_amt],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A20,NM_Claim[TAT],"<=7")/10^5

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A37,NM_Claim[Actionable],"Digit",NM_Claim[Digit_TAT],"<=2")
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A37,NM_Claim[claim_status],"OPEN",NM_Claim[Actionable],"Digit",NM_Claim[TAT],"<=2")





=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[claim_status],"OPEN",NM_Claim[product_lob],Mgmt_Digit!$A37,NM_Claim[Actionable],"Customer",NM_Claim[TAT],">90")
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A37,NM_Claim[claim_status],"OPEN",NM_Claim[Actionable],"Customer",NM_Claim[TAT],"<90")

=TEXT(EOMONTH(Base!$B$1,-3),"MMM-YY")
=TEXT(EOMONTH(Base!$B$1,-3),"MMM-YY")


=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!B$54,"YYYYMM"),NM_Claim[product_lob],Mgmt_Digit!$A55),"-")
=AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],NM_Claim[product_lob],Mgmt_Digit!$A55,NM_Claim[CL Month],TEXT(Mgmt_Digit!B$54,"YYYYMM")


Meaning of below syntax:-
NM_Claim[CL Month], TEXT(Mgmt_Digit!B$54, "YYYYMM")
Convert April 21, 2025 to 202504.
Find all rows in NM_Claim[CL Month] that match 202504.

=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!B$54,"YYYYMM")),"-")
=AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!$B66))


=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Qtr],Mgmt_Digit!F$2,NM_Claim[product_lob],Mgmt_Digit!$A55),"-")
=AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mgmt_Digit!$A55,NM_Claim[CR QTR])



=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!B$54,"YYYYMM"),NM_Claim[product_lob],Mgmt_Digit!$A55),"-")
=IFERROR(AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],TEXT(Mgmt_Digit!N$2,"YYYYMM"),NM_Claim[product_lob],Mgmt_Digit!$A55,NM_Claim[Final Status],"Paid"),"-")



=AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR FY],Mgmt_Digit!J$2)
=AVERAGEIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR FY],Mgmt_Digit!J$54)




=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Qtr],Mgmt_Digit!F$2,NM_Claim[product_lob],Mgmt_Digit!$A55),"-")
=IFERROR(AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Qtr],Mgmt_Digit!R$2,NM_Claim[product_lob],Mgmt_Digit!$A55,NM_Claim[Final Status],"Paid"),"-")

=AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Qtr],Mgmt_Digit!R$54,NM_Claim[Final Status],"Paid")



=IFERROR(AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL FY],Mgmt_Digit!V$2,NM_Claim[product_lob],Mgmt_Digit!$A55,NM_Claim[Final Status],"Paid"),"-")

=EOMONTH(TODAY()-1,-16)+1

=EOMONTH(TODAY()-1,-16)+1

=TEXT(A3,"YYYYMM")*1
=TEXT(A3,"YYYYMM")*1

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CR Month],"<"&DCL!$B3,NM_Claim[CL Month],">="&DCL!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CR Month],"<"&DCL!$B3,NM_Claim[CL Month],"-")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CR Month],"<"&DCL!$B3,NM_Claim[CL Month],">="&DCL!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit_CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CR Month],"<"&DCL!$B3,NM_Claim[CL Month],"-")


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CR Month],DCL!$B3)
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,,NM_Claim[)


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3)

=IF((C3+D3)=0,"-",E3/(C3+D3))
=IF((C3+D3=0,"-",E3/C3+D3))


=IF(E3=0,"-",COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Paid")/E3)

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Zero Paid")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[last_reopen_date],">0")

=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3),"-")



=IFERROR(AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Paid"),"-")
=IFERROR(AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status,"Paid"),"-")


=IFERROR(AVERAGEIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Paid"),"-")

=IFERROR(AC3/SUMIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Paid"),"-")

=SUMIFS(NM_Claim[indemnity_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Paid

=IFERROR(AC3/SUMIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],DCL!$B$1,NM_Claim[CL Month],DCL!$B3,NM_Claim[Final Status],"Paid"),"-")


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CR Month],"<"&Health!$B3,NM_Claim[CL Month],">="&Health!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CR Month],"<"&Health!$B3,NM_Claim[CL Month],"-")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CR Month],"<"&Health!$B3,NM_Claim[CL Month]">="&Health!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CR Month],"<"&Health!$B3,NM_Claim[CL Month],"-")




=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Mobile!$B$1,NM_Claim[CL Month],Mobile!$B3,NM_Claim[Final Status],"Zero Paid",NM_Claim[Zero Paid Reason],Mobile!K$2)
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CL Month],Health!$B3,NM_Claim[Final Status],"Zero Paid",NM_Claim[Zero Paid Reason],Health!K$2)


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CL Month],Health!$B3,NM_Claim[Final Status],"Zero Paid",NM_Claim[Zero Paid Reason],Health!K$2)

=IFERROR(
 AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CL Month],Health!$B3,NM_Claim[indemnity_paid],"<=100000")        ,"-")
=AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Health!$B$1,NM_Claim[CL Month],Health!$B3,NM_Claim[Indemnity_paid],"<=100000")



=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Liability!$B$1,NM_Claim[CR Month],"<"&Liability!$B3,NM_Claim[CL Month],">="&Liability!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Liability!$B$1,NM_Claim[CR Month],"<"&Liability!$B3,NM_Claim[CL Month],"-")


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Liability!$B$1,NM_Claim[CR Month],"<"&Liability!$B3,NM_Claim[CL Month],">="&Liability!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Liability!$B$1,NM_Claim[CR Month],"<"&Liability!$B3,NM_Claim[CL Month],"-")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Liabilty!$B$1,NM_Claim[CR Month],"<"&Liability!$B3,NM_Claim[CL Month],">="&Liability!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Liability!$B$1,NM_Claim[CR Month],"<"&Liability!$B3,NM_Claim[CL Month],"-")



=VLOOKUP(@[movie_id]:[movie_id],Financials,2,FALSE)
=VLOOKUP(Movies@[movie_id],Financials,2,FALSE)


=IF(Movies[@currency]="INR",L2/86.19,L2)

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],"<"&Summary!$B3,NM_Claim[CL Month],">="&Summary!$B3,NM_Claim[product_lob],Summary!C$2)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],"<"&Summary!$B3,NM_Claim[CL Month],"-",NM_Claim[product_lob],Summary!C$2)


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!C$2,NM_Claim[CR Month],"<"&Summary!$B3,NM_Claim[CL Month],">="&Summary!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!C$2,NM_Claim[CR Month],"<"&Summary!$C3,NM_Claim[CL Month],"-")


=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],"<"&Summary!$B3,NM_Claim[CL Month],">="&Summary!$B3)+
COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],"<"&Summary!$B3,NM_Claim[CL Month],"-")

=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CR Month],Summary!$B3,NM_Claim[product_lob],Summary!O$2)
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!O$3,NM_Claim[CR Month],Summary!$B3)


=IF((I3+U3)=0,"-",AF3/(I3+U3))
=IF((G3+S3=0),"-",AE3/(G3+S3))


=IF(N3+Z3)=0,"-",AL3/(N3+Z3))


=IF(AA3=0,"-",COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],Summary!BK$2,NM_Claim[Final Status],"Paid")/AA3)
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!B$K,NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"PAID")/AA3

=IF(AL3=0,"-",COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"Paid")/AL3)


=IF(AA3=0,"-",COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],Summary!BW$2,NM_Claim[Final Status],"Zero Paid")/AM3)
=COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!BW$2,NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"Zero Paid",NM_Claim[Zero Paid Reason],)

=IF(AA3=0,"-",COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],Summary!BW$2,NM_Claim[Final Status],"Zero Paid")/AM3)

=IF(AM3=0,"-",COUNTIFS(NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!BW$2,NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"Zero Paid")/AM3)



=IFERROR(AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],Summary!ED$2,NM_Claim[indemnity_paid],"<=100000"),"-")
=AVERAGEIFS(NM_Claim[TAT],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!ED$2,NM_Claim[CL Month],Summary!$B3,NM_Claim[indemnity_paid],"<=100000")



=SUMIFS(NM_Claim[indemnity_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],Summary!FB$2,NM_Claim[Final Status],"Paid")
=SUMIFS(NM_Claim[indemnity_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!FC$2,NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"PAID")


=        FD3/SUMIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[product_lob],Summary!FB$2,NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"PAID")
=IFERROR(FD3/SUMIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],Summary!FB$2,NM_Claim[Final Status],"Paid"),"-")


=IFERROR(GS3/SUMIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[Final Status],"Paid"),"-")
=IFERROR(GS3/SUMIFS(NM_Claim[net_paid],NM_Claim[coinsurance_flag],"Digit-CL",NM_Claim[CL Month],Summary!$B3,NM_Claim[product_lob],NM_Claim[Final Status],"PAID"),"-")

================================================================================================================================

=VLOOKUP(Z2,Base!$D$2:$E$10,2,1)


=IF(Z2="","-",
RIGHT((YEAR(Z2)+(MONTH(Z2)>=4))-1,2)&
RIGHT((YEAR(Z2)+(MONTH(Z2)>=4))-1,2)+1& 
" Q"&CHOOSE(MONTH(Z2),4,4,4,1,1,1,2,2,2,3,3,3))

Let's break down the expression RIGHT((YEAR(Z2)+(MONTH(Z2)>=4))-1,2) step by step:

YEAR(Z2):

Extracts the year from the date in cell Z2.
MONTH(Z2)>=4:

Checks if the month of the date in Z2 is April or later.
Returns TRUE (1) if the month is April or later, otherwise FALSE (0).
YEAR(Z2) + (MONTH(Z2)>=4):

Adds 1 to the year if the month is April or later, otherwise adds 0.
(YEAR(Z2) + (MONTH(Z2)>=4)) - 1:

Subtracts 1 from the result of the previous step. This effectively adjusts the year based on the fiscal year starting in April.
RIGHT(..., 2):

Extracts the last two digits of the adjusted year.
Example:
If Z2 contains the date 2025-05-15:

YEAR(Z2) returns 2025.
MONTH(Z2)>=4 returns TRUE (1) because May is after April.
YEAR(Z2) + 1 results in 2026.
2026 - 1 results in 2025.
RIGHT(2025, 2) extracts the last two digits, which are "25".
So, RIGHT((YEAR(Z2)+(MONTH(Z2)>=4))-1,2) returns "25".



Formula: Full Explanation 
===========================
=IF(Z2="","-",RIGHT((YEAR(Z2)+(MONTH(Z2)>=4))-1,2)&RIGHT((YEAR(Z2)+(MONTH(Z2)>=4))-1,2)+1&" Q"&CHOOSE(MONTH(Z2),4,4,4,1,1,1,2,2,2,3,3,3))

Explanation:
IF(Z2="", "-", ...):

This part checks if cell Z2 is empty.
If Z2 is empty, it returns "-".
If Z2 is not empty, it proceeds with the rest of the formula.
YEAR(Z2):

Extracts the year from the date in cell Z2.
MONTH(Z2)>=4:

Checks if the month of the date in Z2 is April or later.
Returns TRUE (1) if the month is April or later, otherwise FALSE (0).
YEAR(Z2) + (MONTH(Z2)>=4) - 1:

Adds 1 to the year if the month is April or later, then subtracts 1.
This effectively adjusts the year based on the fiscal year starting in April.
RIGHT(..., 2):

Extracts the last two digits of the adjusted year.
RIGHT(..., 2) + 1:

Adds 1 to the last two digits of the adjusted year.
" Q"&CHOOSE(MONTH(Z2), 4, 4, 4, 1, 1, 1, 2, 2, 2, 3, 3, 3):

Determines the fiscal quarter based on the month of the date in Z2.
CHOOSE function maps the month to the corresponding fiscal quarter:
Months 1, 2, 3 → Q4
Months 4, 5, 6 → Q1
Months 7, 8, 9 → Q2
Months 10, 11, 12 → Q3
Putting It All Together:
If Z2 is empty, the formula returns "-".
Otherwise, it constructs a string with the last two digits of the adjusted year, the next year, and the fiscal quarter.
For example, if Z2 contains 2025-05-15:

The year is 2025.
The month is May (5), which is >= April, so the adjusted year is 2025 + 1 - 1 = 2025.
The last two digits of 2025 are 25.
Adding 1 gives 26.
May corresponds to Q1.
The result is "2526 Q1".



=IF(W2="OPEN","-",VLOOKUP(AB2,Base!$D$2:$E$10,2,1))

=IF(W2="OPEN",,"-",VLOOKUP(AB2,Base!$D$2:$E$10,2,1))

=IF(W2="OPEN","-",RIGHT((YEAR(AB2)+(MONTH(AB2)>=4))-1,2)&RIGHT((YEAR(AB2)+(MONTH(AB2)>=4))-1,2)+1&" Q"&CHOOSE(MONTH(AB2),4,4,4,1,1,1,2,2,2,3,3,3))


=IF([@claim_status]="OPEN","OPEN",IF(AND(W2="Closed",[@indemnity_paid]<=0),"Zero Paid","Paid"))

=IF(
OR(AI2="CO-IN",AI2="RI-IN"),"-",
IF(
AND(AI2="Digit-CL",O2=""),"Not_Tagged",
IF(
AND(AI2="Digit-CL",
OR(O2="Liability",O2="Mobile - Damage",O2="PP Claim",O2="Mobile - Theft",O2="SBI-DC Claims")),"LL_Claim","CL_Claim")))


=IF(
OR(AI2="CO-IN",AI2="RI-IN"),"-",
IF(
AND(AI2="Digit-CL",O2=""),"Not_Tagged",
IF(
AND(AI2="Digit-CL",
OR(O2="Liability",O2="Mobile - Damage",O2="PP Claim",O2="Mobile - Theft",O2="SBI-DC Claims")),"LL_Claim","CL_Claim")))

=IF(G2="OPEN","-",IF(G2="Paid","-",IFNA(IFNA(VLOOKUP([@coverage_reason],Base!$I$1:$J$40,2,0),VLOOKUP([@closing_reason],Base!$M$1:$N$40,2,0)),"TBC")))
=IF(G2="OPEN","-",IF(G2="Paid","-",IFNA(IFNA(VLOOKUP([@coverage_reason],Base!$I$1:$J$16,2,0),VLOOKUP([@closing_reason],Base!$M$1:$N$24,2,0)),"TBC")))

=IF(G2="OPEN",IFERROR(VLOOKUP(P2&Q2,Reason_Base!$J$1:$K$90,2,0),"Digit"),"-")

=IF(W2="OPEN",TODAY()-Z2,AB2-Z2)

=IFERROR(IF(AND(W2="OPEN",ISBLANK((R2))),K2,IF(W2="CLOSED",AB2-Z2,TODAY()-R2)),[@TAT])
If W2 is "OPEN" and R2 is blank, the formula returns the value in K2.
If W2 is "CLOSED", the formula returns the result of AB2 - Z2.
If W2 is neither "OPEN" nor "CLOSED", the formula returns the result of TODAY() - R2.
If any part of the nested IF function results in an error, the formula returns the value in the [@TAT] column.

=IFERROR(IF(AND(W2="OPEN",ISBLANK((R2))),K2,IF(W2="Closed",AB2-Z2,TODAY()-R2)),[@TAT])




=IF(BF2<=7,"1. Below 7 days",IF(BF2<=15,"2. 8 to 15 days",IF(BF2<=30,"3. 16 to 30 days","4. Above 30 days")))

=LOOKUP(BF2, {0, 8, 16, 31}, { "1. Below 7 days",  "2. 8 to 15 days", "3. 16 to 30 days", "4. Above 30 days"})
