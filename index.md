<head>

<title>Cosmology and Calendar</title><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<script language="JavaScript1.2">
<!--

var NS = (document.layers) ? 1 : 0;
var NS6 = (document.getElementById) ? 1 : 0;
var IE = (document.all) ? 1 : 0;

var browser = navigator.appName;
var version = navigator.appVersion;
var bVer = browser + " " + version;

aMonthName = new Array("","Zarantyr","Olarune","Therendor","Eyre","Dravago","Nymm","Lharvion","Barrakas","Rhaan","Sypheros","Aryth","Vult","Frostmantle","Thornrise","Treeborn","Rainsong","Arrowfar","Sunstride","Glitterstream","Havenwild","Stormborn","Harrowfall","Silvermoon","Windwhisper","Aruk","Lurn","Ulbar","Kharn","Ziir","Dwarhuun","Jond","Sylar","Razagul","Thazm","Drakhadur","Uarth","Fang","Wind","Ash","Hunt","Song","Dust","Claw","Blood","Horn","Heart","Spirit","Smoke","January","February","March","April","May","June","July","August","September","October","November","December");

// == PLANAR INFO == Orbit Length (days) == Coterminus/Remote Length == Current Point == Starting Point == Stpecial Condition Tag == Status ========
// == CONDITIONS == 0 = Normal / 1 = Frozen Orbit / 2 = Random / 3 = Special
// == STATUS == 0 = Not Yet Set / 1 = Remote / 2 = Waxing / 3 = Coterminus / 4 = Waning 

aPlanarInfo = new Array("0","0","0","0","0","0","134400","33600","50400","50400","0","0","1","1","0","0","1","0","33600","336","8559","8559","0","0","1680","28","1344","1344","0","0","1008","10","420","420","0","0","0","0","0","0","2","0","364","7","94","94","0","0","1680","3","422","422","0","0","1680","28","505","505","0","0","12096","336","4032","4032","0","0","3360","1","841","841","0","0","75600","2352","20076","20076","0","0","2352000","336","588168","588168","3","0");
//aLunarInfo = new Array(0,28,53,87,142,222,277,311,336);
aLunarInfo = new Array(7,21,34,47,59,75,97,117,165,199,247,267,289,305,317,330,336);

aLunarOrbits = new Array(0,28,35,42,49,56,63,70,77,84,91,98,105);
aLunarOffset = new Array(0,0,1,1,2,2,2,3,3,3,3,4,4);
//aLunarOrbits = new Array(0,77,56,42,63,91,28,98,105,49,35,84,70);
//aLunarStarts = new Array(0,16,44,72,100,128,154,182,210,238,266,294,322);

aLunarPercents = new Array(0,8,8,8,9,8,8,9,8,8,9,8,9);

//aLunarPercents = new Array(0,11,8,8,17,23,17,8,8);
aLunarTotals = new Array(0,0,0,0,0,0,0,0,0,0,0,0,0,0);

// 6 Nymm
// 10 Sypheros
// 3 Therendor
// 9 Rhaan
// 2 Olarune
// 4 Eyre
// 12 Vult
// 1 Zarantyr
// 11 Aryth
// 5 Dravago
// 7 Lharvion
// 8 Barrakas

aMoonName = new Array("","Nymm","Sypheros","Therendor","Rhaan","Olarune","Eyre","Vult","Zarantyr","Aryth","Dravago","Lharvion","Barrakas");


//aMoonName = new Array("","Zarantyr","Olarune","Therendor","Eyre","Dravago","Nymm","Lharvion","Barrakas","Rhaan","Sypheros","Aryth","Vult");

sText = "<font face=\"arial\" size=\"1\">Welcome to the Eberron Cosmology & Calendar Tool. You can enter a Year, Month, or Day in the fields to the left to determine where the planes and phases of the moon will be at that time. The program is based on the data given in the Eberron campaign setting. The year value is based on the YK calendar, a conversion of this number to corespond with the timeline (pages 224-225) will appear when appropriate. For example -1YK is the same as -1000 on the timeline.</font>"
iCalendar = 1;

autocount = 0;
negcount = 0;

xYear = 998;
xMonth = 1;
xDay = 1;

qYear = -2203;
qMonth = 12;
qDay = 28;

iYear = 998;
iMonth = 1;
iDay = 1;

cpc = .66;
Kythri = 0;
KythriCount = 1;
setKythri(cpc);


rnd.today=new Date();
rnd.seed=rnd.today.getTime();

function rnd() {
	rnd.seed = (rnd.seed*9301+49297) % 233280;
	return rnd.seed/(233280.0);
};

function rand(number) {
	return Math.ceil(rnd()*number);
};

// === Set Kythri Cycle ==============

function setKythri(cpc) {

	KythriPhases = Math.floor((Math.random() * 3360) + 1);		
		aPlanarInfo[(37)] = KythriPhases;
	KythriPhases2 = Math.floor((Math.random() * 3360) + 1);	
		Kythri = (KythriPhases * 2) + (KythriPhases2 * 2)		
	aPlanarInfo[(36)] = Kythri;
			KythriStart = Math.floor(Kythri * cpc);	
	aPlanarInfo[(38)] = KythriStart;  
	aPlanarInfo[(39)] = KythriStart;  
	
}		
	
	
	
// ====||| CLICK SET YEAR |||=================================================

function clickSetYear(){
	iYear = parseInt(document.form1.year.value);
//	showPart2(iCalendar);
	showPart3();		
	showPart1();	
	setPlanes();
	movePlanes();
	showPlanes();
	showPart4();	
	showPart5();		

}

// ====||| CLICK SET MONTH |||=================================================

function clickSetMonth(){
	iMonth = parseInt(document.form1.month.value);
//	showPart2(iCalendar);
	showPart3();		
	showPart1();	
	setPlanes();
	movePlanes();
	showPlanes();
	showPart4();
	showPart5();		
	
}

// ====||| SELECTED MONTH |||=================================================

function selectMonth(smon){

	bMon = "";
	if (smon == parseInt(iMonth)) { 
		bMon = "selected";
	}	
	return bMon;	
}

// ====||| CLICK SET DAY |||=================================================

function clickSetDay(){
	iDay = parseInt(document.form1.day.value);
//	showPart2(iCalendar);
	showPart3();		
	showPart1();	
	setPlanes();
	movePlanes();
	showPlanes();
	showPart4();
	showPart5();		
	
}

// ====||| SELECTED DAY |||=================================================

function selectDay(sday){

	bDay = "";
	if (sday == parseInt(iDay)) { 
		bDay = "selected";
	}	
	return bDay;	
}

// ====||| BGCOLOR DAY |||=================================================

function colDay(cday){

	bgDay = "#ffffff";
	if (cday == parseInt(iDay)) { 
		bgDay = "#d7f9c8";
	}	
	return bgDay;	
}

// ====||| CLICK SET CALENDAR |||=================================================

function clickSetCalendar(cset){
	iCalendar = parseInt(document.form2.calendar.value);
//	showPart2(iCalendar);
	showPart3();		
	showPart1();	
	showPlaneInfo(14);	
}

// ====||| SELECT MONTH NAME |||=================================================

function sMonthName(cmon){
	mNum = parseInt(cmon);
	cPos = ((iCalendar - 1) * 12) 
	xNum = mNum + cPos;
	return aMonthName[xNum];
}

// ====||| Timeline Value |||=================================================

function timelineValue(){

	dispYear = ""; 

	if (iYear == 1) {
		dispYear += " (-998)"; 
	}
	
	if (iYear < 1) {
		absYear = Math.abs(iYear);
		dxYear = absYear + 999;
		dispYear += " (-" + dxYear + ")"; 
	} 	

	return dispYear	

}


// ===================================================================================

function setPlanes(){

	for (sps=1; sps<=13; sps++){

		pstart = sps * 6;

		oLength = parseInt(aPlanarInfo[(pstart)]);
		cPoint = parseInt(aPlanarInfo[(pstart + 2)]);
		sPoint = parseInt(aPlanarInfo[(pstart + 3)]);
		xCondition = parseInt(aPlanarInfo[(pstart + 4)]);		

		zYear = iYear - xYear;
		zMonth = iMonth - xMonth;
		zDay = iDay - xDay;
		zDays = (zYear * 336) + (zMonth * 28) + zDay; 	

		totDays = zDays + sPoint;	
		
		absDays = Math.abs(totDays);
	
		oTimes = 0;
		sDays = 0;
		cTest = 0;


		if (absDays > oLength) {
			oTimes = Math.floor(absDays / oLength);
			sDays = oTimes * oLength;
			cTest = 2;
		}

		tDays = absDays - sDays - sPoint  

		xPoint = sPoint + tDays;
		
		aPlanarInfo[(pstart + 2)] = xPoint;		
		
		if (xCondition == 1) {
			aPlanarInfo[(pstart + 2)] = sPoint;
		}		

//		if (xCondition == 2 && cTest == 2) {
//			cpc = Math.abs(xPoint / oLength);
//			if (iYear <=0 ) {
//				cpc = cpc * -1 ;
//			} 
//				setKythri(cpc);
//		}		

//		alerttext = "Difference: " + zDays + " Start: " + sPoint + " Total: " + totDays + " Absolute: " + absDays + "\nCycle: " + oLength + " Loops: " + oTimes + " Excess: " + sDays + " Leftover: " + tDays + " Final: " + xPoint;   	
		
//		alert(alerttext);
		
	}

}


// ===================================================================================

function planeLocation(xplane){

	splane = parseInt(xplane);
	pstart = splane * 6;
	oLength = parseInt(aPlanarInfo[(pstart)]);
	crLength = parseInt(aPlanarInfo[(pstart + 1)]);
	cPoint = parseInt(aPlanarInfo[(pstart + 2)]);
	sPoint = parseInt(aPlanarInfo[(pstart + 3)]);
	xCondition = parseInt(aPlanarInfo[(pstart + 4)]);

	wLength = ((oLength - (2 * crLength)) / 2)

	if (cPoint <= crLength) {    													// Remote
		xCoord = 327;
		aPlanarInfo[(pstart + 5)] = 1;
	} 
	if (cPoint > crLength && cPoint <= (crLength + wLength)){ 						// Waxing
		xCoord = Math.floor(327 + (100 * ((cPoint - crLength) / wLength)));		
		aPlanarInfo[(pstart + 5)] = 2;
	}
	if (cPoint > (crLength + wLength) && cPoint <= ((2 * crLength) + wLength)){ 	// Coterminus
		xCoord = 427;
		aPlanarInfo[(pstart + 5)] = 3;
	}
	if (cPoint > ((2 * crLength) + wLength) && cPoint < oLength){ 				// Waning
		xCoord = Math.floor(427 - (100 * ((cPoint - ((2 * crLength) + wLength)) / wLength)));		
		aPlanarInfo[(pstart + 5)] = 4;
	}	

	return xCoord

}

// ===================================================================================

function planeStatus(pstat){

	splane = parseInt(pstat);
	pstart = splane * 6;
	pStatus = parseInt(aPlanarInfo[(pstart + 5)]);

	planestat = "" 

	if (pStatus == 1) {
		planestat = "<font color=\"#a600a6\">Remote</font>" 
	} 	
	if (pStatus == 2) {
		planestat = "Waxing" 
	} 	
	if (pStatus == 3) {
		planestat = "<font color=\"#008c00\">Coterm.</font>" 
	} 	
	if (pStatus == 4) {
		planestat = "<font color=\"#a5a5a5\">Waning</focus>" 
	} 	

	return planestat

}

// ===================================================================================

function planeStat(pstat){

	splane = parseInt(pstat);
	pstart = splane * 6;
	pStatus = parseInt(aPlanarInfo[(pstart + 5)]);

	return pStatus

}

// ===================================================================================

function planeInfo(zplane){

	splane = parseInt(zplane);
	pstart = splane * 6;
	oLength = parseInt(aPlanarInfo[(pstart)]);
	crLength = parseInt(aPlanarInfo[(pstart + 1)]);
	cPoint = parseInt(aPlanarInfo[(pstart + 2)]);
	sPoint = parseInt(aPlanarInfo[(pstart + 3)]);
	xCondition = parseInt(aPlanarInfo[(pstart + 4)]);
	wLength = ((oLength - (2 * crLength)) / 2)
	aLength = (2 * crLength) + (2 * wLength) 

//		pInfo = aLength + "(" + crLength + "-" + wLength + "-" + crLength + "-" + wLength + ")";      
//		pInfo = "Down Time: " + wLength;      
//		pInfo = "Pos: " + cPoint + " (" + oLength + ")";      

	pStatus = parseInt(aPlanarInfo[(pstart + 5)]);

	pInfo = "" 

	if (pStatus == 1) {
		nxs = 1 + (crLength - cPoint); 
		pInfo = "&nbsp;" + nxs + " days until Waxing."; 
	} 	
	if (pStatus == 2) {
		nxs = 1 + ((crLength + wLength) - cPoint); 
		pInfo = "&nbsp;" + nxs + " days until Coterminous."; 
	} 	
	if (pStatus == 3) {
		nxs = 1 + (((crLength * 2) + wLength) - cPoint); 
		pInfo = "&nbsp;" + nxs + " days until Waning."; 
	} 	
	if (pStatus == 4) {
		nxs = 1 + (aLength - cPoint); 
		pInfo = "&nbsp;" + nxs + " days until Remote."; 
	} 	
	
	if (xCondition == 1) {
		pInfo = "&nbsp;No Information Available"; 
	}		

	if (xCondition == 2) {
		pInfo += "&nbsp;*"; 
	}			

	if (xCondition == 3) {
		pInfo += "&nbsp;**"; 
	}			
	
	
	return pInfo

}

// ===================================================================================

function movePlanes(){

 		for (sp=1; sp<=13; sp++){
			planedispname = "planedisplay" + sp;
			document.getElementById(planedispname).style.left = planeLocation(sp);
		}

}	


// ===================================================================================

function showPlanes(){

		// == STATUS == 0 = Not Yet Set / 1 = Remote / 2 = Waxing / 3 = Coterminus / 4 = Waning 

 		for (sp=1; sp<=13; sp++){
			planedisp = "<img src=\"images/bar_Pointer.gif\">";
			if (planeStat(sp) == 1){
				planedisp = "<img src=\"images/bar_Pointer_P.gif\">";
 			}	
			if (planeStat(sp) == 2){
				planedisp = "<img src=\"images/bar_Pointer.gif\">";
 			}	
			if (planeStat(sp) == 3){
				planedisp = "<img src=\"images/bar_Pointer_G.gif\">";
 			}	
			if (planeStat(sp) == 4){
				planedisp = "<img src=\"images/bar_Pointer_Grey.gif\">";
 			}	
			planedispname = "planedisplay" + sp;
			display(planedispname, planedisp);		
		}	
		
}	

// ===================================================================================

function AutoPlane(){

		iDay = iDay + 1

		if (iDay > 28) {
			iDay = 1;
			iMonth = iMonth + 1;
		}
		if (iMonth > 12) {
			iMonth = 1;
			iYear = iYear + 1;
		}	
		
		setPlanes();	

		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		
		

		autoId = setTimeout('AutoPlane()',1000); 
}

// ===================================================================================

function ReversePlane(){

		iDay = iDay - 1

		if (iDay < 1) {
			iDay = 28;
			iMonth = iMonth - 1;
		}
		if (iMonth < 1) {
			iMonth = 12;
			iYear = iYear - 1;
		}	
		
		setPlanes();		

		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		
		

		autoId2 = setTimeout('ReversePlane()',1000); 
}

// ===================================================================================

function clickStartSkipBack(){


				iYear = iYear - 1;


		setPlanes();		

		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		
		

}

// ===================================================================================

function clickStartSkipForward(){


				iYear = iYear + 1;


		setPlanes();		

		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		
		

}

// ===================================================================================

function clickMonthBack(){

	 	iMonth = iMonth - 1

		
		
		if (iMonth < 1) {
			iMonth = 12;
			if (iYear >=0 ) {
				iYear = iYear - 1;
			} else {
				iYear = iYear + 1;
			}
		}

		setPlanes();		

		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		

}

// ===================================================================================

function clickMonthForward(){

	 	iMonth = iMonth + 1

		if (iMonth > 12) {
			iMonth = 1;
			if (iYear >= 0 ) {
				iYear = iYear + 1;
			} else {
				iYear = iYear - 1;
			}
		}
	
		setPlanes();		

		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		

}

// ===================================================================================

function clickChangeDay(chd){

	 	iDay = parseInt(chd);

		setPlanes();		
		showPart1();
		showPart3();				
		movePlanes();
		showPlanes();
		showPart4();
		showPart5();		

}

// ===================================================================================

function clickStartAuto(no){

	autoId = setTimeout('AutoPlane()',1000); 
	autocount = autocount + 1;
	if (autocount == 2) {
		alertmessage = "Clicking the start button multiple\ntimes will speed up the planes.\nThis may cause your browser to crash.\nTo slow the planes down or bring them to\na stop, click the stop button until it stops.";
		alert(alertmessage);
	}
	
	speedDisp();
	showPart6(2);
	
}

// ===================================================================================

function clickStopAuto(){

	clearTimeout(autoId);
	autocount = autocount - 1;
	if (autocount <= 0) { 
		autocount = 0;
		showPart6(1);
	} 	

	speedDisp();
		
}

// ===================================================================================

function clickStop(){

	clickStopAuto();
	clickStopReverse();
	speedDisp();
		
}

// ===================================================================================

function clickStartReverse(no){

	autoId2 = setTimeout('ReversePlane()',1000); 
	negcount = negcount + 1;
	if (negcount == 2) {
		alertmessage = "Clicking the reverse button multiple\ntimes will speed up the reverse flow of the planes.\nThis may cause your browser to crash.\nTo slow the planes down or bring them to\na stop, click the stop button until it stops.";
		alert(alertmessage);
	}
	
	speedDisp2();
	showPart6(3);
		
}

// ===================================================================================

function clickStopReverse(){

	clearTimeout(autoId2);
	negcount = negcount - 1;
	if (negcount <= 0) { 
		negcount = 0;
		showPart6(1);		
	} 	

	speedDisp2();
}

// ===================================================================================

function speedDisp(){

	speeddisp = "<font size=\"1\" face=\"arial\" color=\"#a6a6a6\">" + autocount + "</font>";
	display("speeddisplay", speeddisp);		
	
}

// ===================================================================================

function speedDisp2(){

	speeddisp2 = "<font size=\"1\" face=\"arial\" color=\"#a6a6a6\">" + negcount + "</font>";
	display("speeddisplay2", speeddisp2);		
	
}

// ===================================================================================

function calcMoonPhase(moon,mmx,mdx){

aLunarTotals = new Array(0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0);
	
	
		if (mmx == ""){
			mmx = iMonth;
		}
		if (mdx == ""){
			mdx = iDay;
		}
	
		oLength = parseInt(aLunarOrbits[moon]);

		zYear = iYear - qYear;
		zMonth = mmx - qMonth;
		zDay = mdx - qDay + aLunarOffset[moon];
		zDays = (zYear * 336) + (zMonth * 28) + zDay; 	
		
//		zYear = iYear;
//		zMonth = iMonth;
//		zDay = iDay;
//		zMonth = mmx;
//		zDay = mdx;


		totDays = zDays; 
		
		absDays = Math.abs(totDays);
	
		oTimes = 0;
		sDays = 0;

		if (absDays > oLength) {
			oTimes = Math.floor(absDays / oLength);
			sDays = oTimes * oLength;
		}

		tDays = absDays - sDays  

		xPoint = tDays;

		xlTemp = 0;		
		xlTotal = 0; 
		
 		for (lt=0; lt<=12; lt++){
			xlTemp = Math.floor(((aLunarPercents[lt] * .01) * aLunarOrbits[moon]) + .5);
//			xlTemp = Math.floor(((aLunarPercents[lt] * .01) * aLunarOrbits[moon]) );
			xlTotal += xlTemp  
			aLunarTotals[lt] = xlTotal  
		}
				
				
if (zDays >= 1) {				
				
	if (xPoint >= aLunarTotals[0] && xPoint <= aLunarTotals[1]) {
		moon = "1";
	}
	if (xPoint > aLunarTotals[1] && xPoint <= aLunarTotals[2]) {
		moon = "2";
	}
	if (xPoint > aLunarTotals[2] && xPoint <= aLunarTotals[3]) {
		moon = "2x";
	}
	if (xPoint > aLunarTotals[3] && xPoint <= aLunarTotals[4]) {
		moon = "3";
	}
	if (xPoint > aLunarTotals[4] && xPoint <= aLunarTotals[5]) {
		moon = "3x";
	}
	if (xPoint > aLunarTotals[5] && xPoint <= aLunarTotals[6]) {
		moon = "4";
	}
	if (xPoint > aLunarTotals[6] && xPoint <= aLunarTotals[7]) {
		moon = "5";
	}
	if (xPoint > aLunarTotals[7] && xPoint <= aLunarTotals[8]) {
		moon = "6";
	}
	if (xPoint > aLunarTotals[8] && xPoint <= aLunarTotals[9]) {
		moon = "6x";
	}
	if (xPoint > aLunarTotals[9] && xPoint <= aLunarTotals[10]) {
		moon = "7";
	}
	if (xPoint > aLunarTotals[10] && xPoint <= aLunarTotals[11]) {
		moon = "7x";
	}
	if (xPoint > aLunarTotals[11] && xPoint <= aLunarTotals[12]) {
		moon = "8";
	}				
	if (xPoint > aLunarTotals[12]) {
		moon = "8";
	}	

}	

if (zDays <= 0) {				

	if (xPoint >= aLunarTotals[0] && xPoint <= aLunarTotals[1]) {
		moon = "8";
	}
	if (xPoint > aLunarTotals[1] && xPoint <= aLunarTotals[2]) {
		moon = "7x";
	}
	if (xPoint > aLunarTotals[2] && xPoint <= aLunarTotals[3]) {
		moon = "7";
	}
	if (xPoint > aLunarTotals[3] && xPoint <= aLunarTotals[4]) {
		moon = "6x";
	}
	if (xPoint > aLunarTotals[4] && xPoint <= aLunarTotals[5]) {
		moon = "6";
	}
	if (xPoint > aLunarTotals[5] && xPoint <= aLunarTotals[6]) {
		moon = "5";
	}
	if (xPoint > aLunarTotals[6] && xPoint <= aLunarTotals[7]) {
		moon = "4";
	}
	if (xPoint > aLunarTotals[7] && xPoint <= aLunarTotals[8]) {
		moon = "3x";
	}
	if (xPoint > aLunarTotals[8] && xPoint <= aLunarTotals[9]) {
		moon = "3";
	}
	if (xPoint > aLunarTotals[9] && xPoint <= aLunarTotals[10]) {
		moon = "2x";
	}
	if (xPoint > aLunarTotals[10] && xPoint <= aLunarTotals[11]) {
		moon = "2";
	}
	if (xPoint > aLunarTotals[11] && xPoint <= aLunarTotals[12]) {
		moon = "1";
	}				
	if (xPoint > aLunarTotals[12]) {
		moon = "1";
	}	
}				
	
	
	return moon
	
}

// === Open Moon Window ==================================================================
function showMoonPhases(mphase) {

	mphase = parseInt(mphase);
	
	sHtml = "";
	sHtml += "<html><head><title>Phases of ";
	sHtml += aMoonName[mphase];
	sHtml += " by Month</title><meta http-equiv=\"Content-Type\" content=\"text/html; charset=iso-8859-1\"></head>"
	sHtml += "<body bgcolor=\"#FFFFFF\" background=\"images/back2.jpg\">"	
	sHtml += "<table width=\"100\" border=\"0\" cellspacing=\"1\" cellpadding=\"0\" bgcolor=\"#000000\">";
	sHtml += "<tr><td>";
	sHtml += "<table width=\"600\" border=\"0\" cellspacing=\"2\" cellpadding=\"2\" bgcolor=\"#CCCCCC\" background=\"images/grey_dot.jpg\">";
	sHtml += "<tr align=\"center\" bgcolor=\"#E6E6E6\">"; 
	sHtml += "<td colspan=\"29\" background=\"images/grey_dot3.jpg\">";
	sHtml += "<div align=\"center\"><b><font size=\"6\" face=\"Arial, Helvetica, sans-serif\">Phases of ";
	sHtml += aMoonName[mphase];
	sHtml += " by Month</font></b></div>";
	sHtml += "</td></tr><tr>"; 
	sHtml += "<td bgcolor=\"#FFFFB7\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Month</font></b></td>";
		for (dx=1; dx<=28; dx++){
			sHtml += "<td bgcolor=\"#FFFFB7\">"; 
			sHtml += "<div align=\"center\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">";
			sHtml += dx;
			sHtml += "</font></b></div></td>";
		}
	sHtml += "</tr>";
	
	for (mx=1; mx<=12; mx++){
		sHtml += "<tr align=\"left\" valign=\"top\">"; 
			sHtml += "<td bgcolor=\"#FFFFFF\" width=\"114\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">";
			sHtml += sMonthName(mx);
			sHtml += "</font></td>";
		for (dx=1; dx<=28; dx++){
			sHtml += "<td bgcolor=\"#FFFFFF\" width=\"114\"><img src=\"images/Moon_";
			sHtml += calcMoonPhase(mphase,mx,dx);	
			sHtml += ".jpg\" width=\"18\" height=\"18\"></td>";
		}
		sHtml += "</tr>";		
	}

	sHtml += "<tr align=\"left\" valign=\"top\" bgcolor=\"#E6E6E6\" background=\"images/grey_dot3.jpg\">"; 
	sHtml += "<td width=\"3306\" colspan=\"29\">"; 
	sHtml += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">?? 2004 Wizards of the Coast, Inc., a division of Hasbro, Inc. All rights reserved.</font></div>";
	sHtml += "</td></tr></table></td></tr></table>";
	sHtml += "</body></html>";
	
	oWindow = window.open("","","width=760,height=405,menubar=yes,scrollbars=no,resizable=yes");
	oWindow.document.open();
	oWindow.document.write(sHtml);
	oWindow.document.close();
	oWindow.document.focus();	
	
}

// === Open Moons By Month Window ==================================================================
function showMonthPhases() {

	mxm = iMonth;

	sHtml = "";
	sHtml += "<html><head><title>Moon phases for the month of ";
	sHtml += sMonthName(mxm);
	sHtml += "</title><meta http-equiv=\"Content-Type\" content=\"text/html; charset=iso-8859-1\"></head>"
	sHtml += "<body bgcolor=\"#FFFFFF\" background=\"images/back2.jpg\">"	
	sHtml += "<table width=\"100\" border=\"0\" cellspacing=\"1\" cellpadding=\"0\" bgcolor=\"#000000\">";
	sHtml += "<tr><td>";
	sHtml += "<table width=\"600\" border=\"0\" cellspacing=\"2\" cellpadding=\"2\" bgcolor=\"#CCCCCC\" background=\"images/grey_dot.jpg\">";
	sHtml += "<tr align=\"center\" bgcolor=\"#E6E6E6\">"; 
	sHtml += "<td colspan=\"29\" background=\"images/grey_dot3.jpg\">";
	sHtml += "<div align=\"center\"><b><font size=\"6\" face=\"Arial, Helvetica, sans-serif\">Moon phases for the month of ";
	sHtml += sMonthName(mxm);
	sHtml += "</font>";
	sHtml += "</b></div>";
	sHtml += "</td></tr><tr>"; 
	sHtml += "<td bgcolor=\"#FFFFB7\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Moon</font></b></td>";
		for (dx=1; dx<=28; dx++){
			sHtml += "<td bgcolor=\"#FFFFB7\">"; 
			sHtml += "<div align=\"center\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">";
			sHtml += dx;
			sHtml += "</font></b></div></td>";
		}
	sHtml += "</tr>";
	
	for (mx=1; mx<=12; mx++){
		sHtml += "<tr align=\"left\" valign=\"top\">"; 
			sHtml += "<td bgcolor=\"#FFFFFF\" width=\"114\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">";
			sHtml += aMoonName[mx];
			sHtml += "</font></td>";
		for (dx=1; dx<=28; dx++){
			sHtml += "<td bgcolor=\"#FFFFFF\" width=\"114\"><img src=\"images/Moon_";
			sHtml += calcMoonPhase(mx,mxm,dx);	
			sHtml += ".jpg\" width=\"18\" height=\"18\"></td>";
		}
		sHtml += "</tr>";		
	}

	sHtml += "<tr align=\"left\" valign=\"top\" bgcolor=\"#E6E6E6\" background=\"images/grey_dot3.jpg\">"; 
	sHtml += "<td width=\"3306\" colspan=\"29\">"; 
	sHtml += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">?? 2004 Wizards of the Coast, Inc., a division of Hasbro, Inc. All rights reserved.</font></div>";
	sHtml += "</td></tr></table></td></tr></table>";
	sHtml += "</body></html>";
	
	oWindow = window.open("","","width=760,height=405,menubar=yes,scrollbars=no,resizable=yes");
	oWindow.document.open();
	oWindow.document.write(sHtml);
	oWindow.document.close();
	oWindow.document.focus();	
	
}

// === Open Moons By Month Window ==================================================================
function showPrintMonth() {

	mxm = iMonth;

	sHtml = "";
	sHtml += "<html><head><title>";
	sHtml += sMonthName(mxm);
	sHtml += " " + iYear + " YK";
	sHtml += "</title><meta http-equiv=\"Content-Type\" content=\"text/html; charset=iso-8859-1\"></head>";
	sHtml += "<body bgcolor=\"#FFFFFF\">";	
	sHtml += "<table border=\"0\" cellspacing=\"1\" cellpadding=\"0\" bgcolor=\"#000000\" width=\"600\" background=\"images/black.gif\">";
	sHtml += "<tr><td>";
	sHtml += "<table width=\"600\" border=\"0\" cellspacing=\"2\" cellpadding=\"2\" bgcolor=\"#CCCCCC\" background=\"images/grey_dot.jpg\">";
	sHtml += "<tr align=\"center\">"; 
	sHtml += "<td colspan=\"7\" bgcolor=\"#E6E6E6\" background=\"images/grey_dot3.jpg\">"; 
	sHtml += "<div align=\"center\"><b><font size=\"6\" face=\"Arial, Helvetica, sans-serif\">";
	sHtml += sMonthName(mxm);
	sHtml += " / ";
	sHtml += iYear;
	sHtml += "<font size=\"3\"> YK</font></font></b></div>";
	sHtml += "</td></tr><tr bgcolor=\"#F2F2F2\">";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Sul</font></b></font></div></td>";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Mol</font></b></font></div></td>";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Zol</font></b></font></div></td>";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Wir</font></b></font></div></td>";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Zor</font></b></font></div></td>";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Far</font></b></font></div></td>";
	sHtml += "<td><div align=\"center\"><font size=\"4\"><b><font face=\"Arial, Helvetica, sans-serif\">Sar</font></b></font></div></td>";
 	sHtml += "</tr>";	

	for (fx=1; fx<=4; fx++){
 	sHtml += "<tr align=\"left\" valign=\"top\">"; 
		for (dx=1; dx<=7; dx++){
			dxd = ((fx - 1) * 7) + dx;
			sHtml += "<td bgcolor=\"#FFFFFF\" width=\"114\"> <font size=\"3\"><b><font face=\"Arial, Helvetica, sans-serif\">";
			sHtml += dxd;
			sHtml += "</font><font face=\"Arial, Helvetica, sans-serif\" color=\"#FFFFFF\"><img src=\"images/white.jpg\" width=\"13\" height=\"70\" align=\"right\"></font></b></font></td>";
		}
	sHtml += "</tr>";
	}

	sHtml += "<tr align=\"left\" valign=\"top\">"; 
	sHtml += "<td bgcolor=\"#FFFFFF\" colspan=\"7\"><font size=\"3\"><b><font face=\"Arial, Helvetica, sans-serif\" color=\"#FFFFFF\"><img src=\"images/white.jpg\" width=\"590\" height=\"300\"></font></b></font></td>";
	sHtml += "</tr></table></td></tr></table>";
		
	sHtml += "</body></html>";
	
	oWindow = window.open("","","width=640,height=770,menubar=yes,scrollbars=yes,resizable=yes");
	oWindow.document.open();
	oWindow.document.write(sHtml);
	oWindow.document.close();
	oWindow.document.focus();	
	
}

// ===================================================================================

function showPart1a(){

   document.form1.day.value = iDay;	

}   
   
function showPart1(){

		pagedisp = "";

		pagedisp += "<form method=\"\" action=\"\" name=\"form1\">";
		pagedisp += "<table width=\"178\" border=\"0\" cellspacing=\"2\" cellpadding=\"2\">";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"right\" width=\"26%\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"3\">Year</font></b></td>";
		pagedisp += "<td width=\"74%\"> ";
		pagedisp += "<input type=\"text\" name=\"year\" size=\"5\" maxlength=\"8\" value=\"" + iYear + "\" onChange=\"clickSetYear(value)\">";
		pagedisp += "<font size=\"1\" face=\"Arial, Helvetica, sans-serif\">YK " + timelineValue() + "</font></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"right\" width=\"26%\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"3\">Month</font></b></td>";
		pagedisp += "<td width=\"74%\"> ";
		pagedisp += "<select name=\"month\" onChange=\"clickSetMonth(value)\">";

		
		pagedisp += "<option value=\"1\" " + selectMonth(1) + ">";
		pagedisp += sMonthName(1);
		pagedisp += "</option>";
		pagedisp += "<option value=\"2\" " + selectMonth(2) + ">";
		pagedisp += sMonthName(2);
		pagedisp += "</option>";
		pagedisp += "<option value=\"3\" " + selectMonth(3) + ">"
		pagedisp += sMonthName(3);
		pagedisp += "</option>";
		pagedisp += "<option value=\"4\" " + selectMonth(4) + ">";
		pagedisp += sMonthName(4);
		pagedisp += "</option>";
		pagedisp += "<option value=\"5\" " + selectMonth(5) + ">";
		pagedisp += sMonthName(5);
		pagedisp += "</option>";
		pagedisp += "<option value=\"6\" " + selectMonth(6) + ">";
		pagedisp += sMonthName(6);
		pagedisp += "</option>";
		pagedisp += "<option value=\"7\" " + selectMonth(7) + ">";
		pagedisp += sMonthName(7);
		pagedisp += "</option>";
		pagedisp += "<option value=\"8\" " + selectMonth(8) + ">";
		pagedisp += sMonthName(8);
		pagedisp += "</option>";
		pagedisp += "<option value=\"9\" " + selectMonth(9) + ">";
		pagedisp += sMonthName(9);
		pagedisp += "</option>";
		pagedisp += "<option value=\"10\" " + selectMonth(10) + ">";
		pagedisp += sMonthName(10);
		pagedisp += "</option>";
		pagedisp += "<option value=\"11\" " + selectMonth(11) + ">";
		pagedisp += sMonthName(11);
		pagedisp += "</option>";
		pagedisp += "<option value=\"12\" " + selectMonth(12) + ">";
		pagedisp += sMonthName(12);
		pagedisp += "</option>";
		
		
		
		
		pagedisp += "</select>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"right\" width=\"26%\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"3\">Day</font></b></td>";
		pagedisp += "<td width=\"74%\"> ";
		pagedisp += "<select name=\"day\" onChange=\"clickSetDay(value)\">";
		pagedisp += "<option value=\"1\" " + selectDay(1) + ">1</option>";
		pagedisp += "<option value=\"2\" " + selectDay(2) + ">2</option>";
		pagedisp += "<option value=\"3\" " + selectDay(3) + ">3</option>";
		pagedisp += "<option value=\"4\" " + selectDay(4) + ">4</option>";
		pagedisp += "<option value=\"5\" " + selectDay(5) + ">5</option>";
		pagedisp += "<option value=\"6\" " + selectDay(6) + ">6</option>";
		pagedisp += "<option value=\"7\" " + selectDay(7) + ">7</option>";
		pagedisp += "<option value=\"8\" " + selectDay(8) + ">8</option>";
		pagedisp += "<option value=\"9\" " + selectDay(9) + ">9</option>";
		pagedisp += "<option value=\"10\" " + selectDay(10) + ">10</option>";
		pagedisp += "<option value=\"11\" " + selectDay(11) + ">11</option>";
		pagedisp += "<option value=\"12\" " + selectDay(12) + ">12</option>";
		pagedisp += "<option value=\"13\" " + selectDay(13) + ">13</option>";
		pagedisp += "<option value=\"14\" " + selectDay(14) + ">14</option>";
  		pagedisp += "<option value=\"15\" " + selectDay(15) + ">15</option>";
		pagedisp += "<option value=\"16\" " + selectDay(16) + ">16</option>";
		pagedisp += "<option value=\"17\" " + selectDay(17) + ">17</option>";
		pagedisp += "<option value=\"18\" " + selectDay(18) + ">18</option>";
		pagedisp += "<option value=\"19\" " + selectDay(19) + ">19</option>";
		pagedisp += "<option value=\"20\" " + selectDay(20) + ">20</option>";
		pagedisp += "<option value=\"21\" " + selectDay(21) + ">21</option>";
		pagedisp += "<option value=\"22\" " + selectDay(22) + ">22</option>";
		pagedisp += "<option value=\"23\" " + selectDay(23) + ">23</option>";
		pagedisp += "<option value=\"24\" " + selectDay(24) + ">24</option>";
		pagedisp += "<option value=\"25\" " + selectDay(25) + ">25</option>";
		pagedisp += "<option value=\"26\" " + selectDay(26) + ">26</option>";
		pagedisp += "<option value=\"27\" " + selectDay(27) + ">27</option>";
		pagedisp += "<option value=\"28\" " + selectDay(28) + ">28</option>";
		pagedisp += "</select>";
		pagedisp += "</td>";
		pagedisp += "</tr>";

		pagedisp += "<tr> ";
		pagedisp += "<td align=\"center\" width=\"100%\" colspan=\"2\"><img src=\"images/accept.jpg\"></td>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		
		
		pagedisp += "</table>";
		pagedisp += "</form>";

		display("pagedisplay1", pagedisp);
}

// ===================================================================================

function showPlaneInfo(xpx){

	sText = "";

	if (xpx == 1) {
		sText += "<font face=\"arial\" size=\"2\"><b>Daanvi, the Perfect Order</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Daanvi is coterminous to the Material Plane for one century every four.<br/><br/>REMOTE: Daanvi is remote for one century every four, seperated from itrs coterminous period by a century.</font>";
	}
	if (xpx == 2) {
		sText += "<font face=\"arial\" size=\"2\"><b>Dal Quor, the Region of Dreams</b></font><font face=\"arial\" size=\"1\"><br/><br/>REMOTE: Dal Quor last became coterminous to the Material Plane some forty thousand years ago, at which time the quori invaded Xan'drik, The giants of Xen'drik finally managed to end the war and sever the connections between the planes, but at great cost: The devastation of Xen'drik and decimation of the civilization of the giants. In the process, Dal Quor itself was thrown off its orbit. As a result, Dal Quor is always remote in relation to the Material Plane. The only way to reach Dal Quor from the Material Plane is through the psychic projection of dreaming, and the quori have been forced to find new ways to work their will on the Material Plane.</font>";
	}
	if (xpx == 3) {
		sText += "<font face=\"arial\" size=\"2\"><b>Dolurrh, the Realm of the Dead</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Dolurrh is coterminous for a period of one year every century, precisely fifty years after being remote.<br/><br/>REMOTE: Dolurrh is remote for a period of one year every century, precisely fifty years after each coterminous phase.</font>";
	}
	if (xpx == 4) {
		sText += "<font face=\"arial\" size=\"2\"><b>Fernia, the Sea of Fire</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Fernia is coterminous to the Material Plane for one month (the midsummer month of " + sMonthName(7) + ") every five years.<br/><br/>REMOTE: Fernia is remote to the Material Plane for one month (the midwinter month of " + sMonthName(1) + ") every five years, two and a half years after each coterminous phase.</font>";
	}
	if (xpx == 5) {
		sText += "<font face=\"arial\" size=\"2\"><b>Irian, the Eternal Day</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Irian is coterminous for a period of ten days in the springtime month of " + sMonthName(4) + ", once every three years.<br/><br/>REMOTE: Irian is remote for a period of ten days in the autumn month of " + sMonthName(10) + " once every three years, a year and a half after each coterminous phase. </font>";
	}
	if (xpx == 6) {
		sText += "<font face=\"arial\" size=\"2\"><b>Kythri, the Churning Chaos</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: True to the plane's chaotic nature, Kytheri's movement through the Astral Plane is utterly erratic, entering a coterminous phase at apparantly random intervals and remaining in that state for anywhere from a day to a century.<br/><br/>* Although not entirely accurate, this tool generates a random period for the coterminous/remote phases and the waxing/waning phases of Kythri when initially launched. Each cycle then follows the numbers determined at launch for each cycle.</font>";
	}
	if (xpx == 7) {
		sText += "<font face=\"arial\" size=\"2\"><b>Lamannia, the Twilight Forest</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Lamannia is coterminous for a period of one week every twelve months.<br/><br/>REMOTE: Lamannia is remote for a period of one week every twelve months, exactally six months after each coterminous phase.</font>";
	}
	if (xpx == 8) {
		sText += "<font face=\"arial\" size=\"2\"><b>Mabar, the Endless Night</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Mabar enters a coterminous phase for three dark knights once every five years, on the nights of the new moon closest to the winter solstice.<br/><br/>REMOTE: Mabar is remote for a period of five autumn days once every five years, around the full moon nearest the summer solstice, two and a half years after each coterminous phase.</font>";
	}
	if (xpx == 9) {
		sText += "<font face=\"arial\" size=\"2\"><b>Risia, the Plane of Ice</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Risia is coterminous to the Material Plane during the midwinter month of " + sMonthName(1) + ", once every five years.<br/><br/>REMOTE: Risia is remote from the Material Plane during the midsummer month of " + sMonthName(7) + ", once every five years, two and a half years after each coterminous phase.</font>";
	}
	if (xpx == 10) {
		sText += "<font face=\"arial\" size=\"2\"><b>Shavarath, the Battleground</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Shavarath is coterminous to the Material Plane for one year out of every thirty-six years.</font>";
	}
	if (xpx == 11) {
		sText += "<font face=\"arial\" size=\"2\"><b>Syrania, the Azure Sky</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Syrania is coterminous to the Material Plane for one day every ten years.<br/><br/>REMOTE: Syranis is remote for one day every ten years, five years after each coterminous phase.</font>";
	}
	if (xpx == 12) {
		sText += "<font face=\"arial\" size=\"2\"><b>Thelanis, the Faerie Court</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: Thelanis is coterminous for a period of seven years every 225 years. When its coterminous phase end, the plane travels in its orbit for 102 years before becoming remote.<br/><br/>REMOTE: Thelanis is remote for a period of fourteen years every 225 years. When its remote the phase ends, the plane travels in its orbit for 102 years before becoming coterminous. </font>";
	}
	if (xpx == 13) {
		sText += "<font face=\"arial\" size=\"2\"><b>Xoriat, the Realm of Madness</b></font><font face=\"arial\" size=\"1\"><br/><br/>COTERMINOUS: The intervention of the Gatekeepers during Xoriat's last coterminous phase altered the plane's orbit, and Xoriat has not been coterminous again since then.<br/><br/>** For the pourposes of this tool, Xoriat was given an extremely long cycle of 2,352,000 days with coterminous and remote periods of one year.</font>";
	}												

	if (xpx == 14) {
		sText += "<font face=\"arial\" size=\"2\"><b>Month Names</b></font><font face=\"arial\" size=\"1\"><br/><br/>The common calendar of Korvaire is the Galifar Calandar. However the druids of the Eldeen Reaches devised Common variants of these names specifically for the months (but not the moons)> Ancient dwarves had their own names for the months, but these are seldom used in modern day. The Talenta halflings use different names for the months because, well they don't like falling in line.<br/><br/>You may select the standard calendar, druid, dwarven, halfling, and even the generic human names for the months by the use of the dropdown at the bottom of this tool. This will cause all references to month names to change to match the chosen type.</font>";
	}		
	
	showPart2(sText);

}

// ===================================================================================

function showPart2(sText){

		pagedisp = "";

		pagedisp += "<table width=\"250\" border=\"0\" cellspacing=\"2\" cellpadding=\"0\" bgcolor=\"#CCCCCC\">";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td width=\"232\"> ";

		pagedisp += "<div class=\"Scroll\">";
		pagedisp += "<table width=\"100%\" border=\"0\" cellspacing=\"1\" cellpadding=\"1\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<tr align=\"left\" valign=\"top\"> ";
		pagedisp += "<td> ";

		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + sText + "</font>";

		pagedisp += "</td>";
		pagedisp += "<td width=\"1\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/white.jpg\" width=\"1\" height=\"131\"></font></td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";
		pagedisp += "</div>";
		
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";

			  	
		display("pagedisplay2", pagedisp);
}

// ===================================================================================

function showPart3(){

		pagedisp = "";

		pagedisp += "<table width=\"150\" border=\"0\" cellspacing=\"2\" cellpadding=\"2\" bgcolor=\"#CCCCCC\">";
		pagedisp += "<tr> ";
		pagedisp += "<td colspan=\"7\" bgcolor=\"#E6E6E6\"> ";
		pagedisp += "<div align=\"center\"><b><font size=\"2\" face=\"Arial, Helvetica, sans-serif\">";
		pagedisp += sMonthName(iMonth);
		pagedisp += "&nbsp;&nbsp;&nbsp;" + iYear + "<font size=\"1\"> YK</font>";
		pagedisp += "</font></b></div>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">S</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">M</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">Z</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">W</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">Z</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">F</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td bgcolor=\"#FFFFB7\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">S</font></div>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(1)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(1) + "'\" bgcolor=\"" + colDay(1) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">1</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(2)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(2) + "'\" bgcolor=\"" + colDay(2) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">2</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(3)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(3) + "'\" bgcolor=\"" + colDay(3) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">3</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(4)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(4) + "'\" bgcolor=\"" + colDay(4) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">4</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(5)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(5) + "'\" bgcolor=\"" + colDay(5) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">5</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(6)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(6) + "'\" bgcolor=\"" + colDay(6) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">6</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(7)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(7) + "'\" bgcolor=\"" + colDay(7) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">7</font></div>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(8)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(8) + "'\" bgcolor=\"" + colDay(8) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">8</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(9)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(9) + "'\" bgcolor=\"" + colDay(9) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">9</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(10)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(10) + "'\" bgcolor=\"" + colDay(10) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">10</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(11)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(11) + "'\" bgcolor=\"" + colDay(11) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">11</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(12)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(12) + "'\" bgcolor=\"" + colDay(12) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">12</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(13)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(13) + "'\" bgcolor=\"" + colDay(13) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">13</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(14)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(14) + "'\" bgcolor=\"" + colDay(14) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">14</font></div>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(15)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(15) + "'\" bgcolor=\"" + colDay(15) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">15</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(16)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(16) + "'\" bgcolor=\"" + colDay(16) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">16</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(17)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(17) + "'\" bgcolor=\"" + colDay(17) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">17</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(18)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(18) + "'\" bgcolor=\"" + colDay(18) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">18</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(19)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(19) + "'\" bgcolor=\"" + colDay(19) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">19</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(20)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(20) + "'\" bgcolor=\"" + colDay(20) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">20</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(21)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(21) + "'\" bgcolor=\"" + colDay(21) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">21</font></div>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(22)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(22) + "'\" bgcolor=\"" + colDay(22) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">22</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(23)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(23) + "'\" bgcolor=\"" + colDay(23) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">23</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(24)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(24) + "'\" bgcolor=\"" + colDay(24) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">24</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(25)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(25) + "'\" bgcolor=\"" + colDay(25) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">25</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(26)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(26) + "'\" bgcolor=\"" + colDay(26) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">26</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(27)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(27) + "'\" bgcolor=\"" + colDay(27) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">27</font></div>";
		pagedisp += "</td>";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:clickChangeDay(28)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='" + colDay(28) + "'\" bgcolor=\"" + colDay(28) + "\"> ";
		pagedisp += "<div align=\"center\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">28</font></div>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"center\" colspan=\"7\" bgcolor=\"#E6E6E6\"> ";
		pagedisp += "<font size=\"1\"><a href=\"javascript:clickMonthBack()\"><img src=\"images/month_l.jpg\" border=\"0\" alt=\"Back 1 Month\" ></a><img src=\"images/grey_dot3.jpg\" width=\"7\" height=\"5\"><a href=\"javascript:clickMonthForward()\"><img src=\"images/month_r.jpg\" border=\"0\"alt=\"Forward 1 Month\" ></a><img src=\"images/grey_dot3.jpg\" width=\"64\" height=\"5\"><a href=\"javascript:showMonthPhases()\"><img src=\"images/tiny_moon.jpg\" border=\"0\" alt=\"Moon Phases This Month\" ></a><img src=\"images/grey_dot3.jpg\" width=\"7\" height=\"5\"><a href=\"javascript:showPrintMonth()\"><img src=\"images/month_icon.jpg\" border=\"0\" alt=\"Printer Friendly Calendar\" ></a></font>";
 		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";
			  	
		display("pagedisplay3", pagedisp);
}





// ===================================================================================

function showPart4(){

		pagedisp = "";

		pagedisp += "<table width=\"435\" border=\"0\" cellspacing=\"1\" cellpadding=\"0\" bgcolor=\"#CCCCCC\">";
		pagedisp += "<tr> ";
		pagedisp += "<td> ";
		pagedisp += "<table width=\"100%\" border=\"0\" cellspacing=\"1\" cellpadding=\"1\" bgcolor=\"#CCCCCC\">";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"center\" bgcolor=\"#E6E6E6\" width=\"59\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Plane</font></b></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#E6E6E6\" width=\"50\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Status</font></b><font size=\"1\" color=\"#CCCCCC\">-</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#E6E6E6\" width=\"216\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/grey_dot3.jpg\" width=\"1\" height=\"5\"></font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#E6E6E6\" width=\"134\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/grey_dot3.jpg\" width=\"134\" height=\"5\"></font></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(1)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Daanvi</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeStatus(1) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(1) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(2)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Dal Quor</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeStatus(2) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(2) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(3)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Dolurrh</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeStatus(3) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(3) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(4)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Fernia</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(4) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(4) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(5)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Irian</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(5) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(5) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(6)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Kythri</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(6) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(6) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(7)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Lamannia</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(7) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(7) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(8)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Mabar</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(8) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(8) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\"   bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(9)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Risia</font></td>";
		pagedisp += "<td align=\"center\"   bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(9) + "</font></td>";
		pagedisp += "<td align=\"left\"   bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(9) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(10)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Shavarath</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(10) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(10) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(11)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Syrania</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(11) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(11) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(12)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Thelanis</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(12) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(12) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr> ";		
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\" style=\"cursor:hand\" onclick=\"javascript:showPlaneInfo(13)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" ><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Xoriat</font></td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><font face=\"Arial, Helvetica, sans-serif\" size=\"1\" >" + planeStatus(13) + "</font></td>";
		pagedisp += "<td align=\"left\" bgcolor=\"#FFFFFF\">";
		pagedisp += "<font face=\"Arial, Helvetica, sans-serif\" size=\"1\">" + planeInfo(13) + "</font>";
		pagedisp += "</td>";
		pagedisp += "<td align=\"center\" bgcolor=\"#FFFFFF\"><img src=\"images/bar_L_end.jpg\" width=\"7\" height=\"18\"><img src=\"images/bar_purple.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_White.jpg\" width=\"100\" height=\"18\"><img src=\"images/bar_green.jpg\" width=\"10\" height=\"18\"><img src=\"images/bar_R_end.jpg\" width=\"7\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";

		display("pagedisplay4", pagedisp);
}

// ===================================================================================

function showPart5(){

		pagedisp = "";

		pagedisp += "<table width=\"150\" border=\"0\" cellspacing=\"0\" cellpadding=\"1\" bgcolor=\"#CCCCCC\">";
		pagedisp += "<tr> ";
		pagedisp += "<td> ";
		pagedisp += "<table width=\"100%\" border=\"0\" cellspacing=\"1\" cellpadding=\"1\" bgcolor=\"#CCCCCC\">";
		pagedisp += "<tr> ";
		pagedisp += "<td align=\"center\" width=\"57%\" bgcolor=\"#E6E6E6\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Moon</font></b></td>";
		pagedisp += "<td align=\"center\" width=\"43%\" bgcolor=\"#E6E6E6\"><b><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">Phase</font></b></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(1)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[1] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(1,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(2)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[2] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(2,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(3)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[3] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(3,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(4)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[4] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(4,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(5)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[5] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(5,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(6)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[6] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(6,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(7)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[7] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(7,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(8)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[8] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(8,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(9)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[9] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(9,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(10)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[10] + "</font></td>";
 		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(10,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(11)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[11] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(11,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td style=\"cursor:hand\" onclick=\"javascript:showMoonPhases(12)\" onmouseover=\"this.style.backgroundColor='#ffb0ff'\" onmouseout=\"this.style.backgroundColor='#FFFFFF'\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\">" + aMoonName[12] + "</font></td>";
		pagedisp += "<td align=\"center\" width=\"43%\"><img src=\"images/Moon_" + calcMoonPhase(12,0,0) + ".jpg\" width=\"18\" height=\"18\"></td>";
		pagedisp += "</tr>";
		pagedisp += "<tr bgcolor=\"#FFFFFF\"> ";
		pagedisp += "<td bgcolor=\"#E6E6E6\" align=\"left\" width=\"57%\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/grey_dot3.jpg\" width=\"13\" height=\"18\"></font></td>";
		pagedisp += "<td bgcolor=\"#E6E6E6\" align=\"center\" width=\"43%\" height=\"18\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/grey_dot3.jpg\" width=\"13\" height=\"18\"></font></td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";
		pagedisp += "</td>";
		pagedisp += "</tr>";
		pagedisp += "</table>";
			  	
		display("pagedisplay5", pagedisp);
}




// ===================================================================================

function showPart6(spvi){

	xpart = parseInt(spvi);
	pagedisp = "";
	
	if (xpart == 1) {	
		pagedisp += "<a href=\"javascript:clickStartSkipBack()\"><img src=\"images/skip_b1.jpg\" border=\"0\" alt=\"Year Back\" width=\"18\" height=\"18\"></a><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStartReverse()\"><img src=\"images/reverse1.jpg\" border=\"0\" alt=\"Automated Back 1 Day\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStop()\"><img src=\"images/stop1.jpg\" border=\"0\" alt=\"Stop Automation\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStartAuto()\"><img src=\"images/start1.jpg\" border=\"0\" alt=\"Automated Forward 1 Day\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStartSkipForward()\"><img src=\"images/skip_f1.jpg\" border=\"0\" alt=\"Year Forward\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"17\" height=\"18\"></font>";
	}
	if (xpart == 2) {	
		pagedisp += "<img src=\"images/skip_b.jpg\" alt=\"Year Back\" width=\"18\" height=\"18\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><img src=\"images/reverse.jpg\" border=\"0\" alt=\"Automated Back 1 Day\" width=\"18\" height=\"18\"><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStopAuto()\"><img src=\"images/stop1.jpg\" border=\"0\" alt=\"Stop Automation\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStartAuto()\"><img src=\"images/start1.jpg\" border=\"0\" alt=\"Automated Forward 1 Day\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><img src=\"images/skip_f.jpg\" alt=\"Year Forward\" width=\"18\" height=\"18\"><img src=\"images/white.jpg\" width=\"17\" height=\"18\"></font>";
	}
	if (xpart == 3) {	
		pagedisp += "<img src=\"images/skip_b.jpg\" alt=\"Year Back\" width=\"18\" height=\"18\"><font face=\"Arial, Helvetica, sans-serif\" size=\"2\" color=\"#FFFFFF\"><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStartReverse()\"><img src=\"images/reverse1.jpg\" border=\"0\" alt=\"Automated Back 1 Day\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><a href=\"javascript:clickStopReverse()\"><img src=\"images/stop1.jpg\" border=\"0\" alt=\"Stop Automation\" width=\"18\" height=\"18\"></a><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><img src=\"images/start.jpg\" border=\"0\" alt=\"Automated Forward 1 Day\" width=\"18\" height=\"18\"><img src=\"images/white.jpg\" width=\"5\" height=\"18\"><img src=\"images/skip_f.jpg\" alt=\"Year Forward\" width=\"18\" height=\"18\"><img src=\"images/white.jpg\" width=\"17\" height=\"18\"></font>";
	}
	
	display("pagedisplay6", pagedisp);

}

// ===================================================================================

function display(id, str) {
  if (NS) {
    with (document[id].document) {
	  open();
      write(str);
      close();
    }
  } else if (NS6) {
    document.getElementById(id).innerHTML = str;
  }	else {
    document.all[id].innerHTML = str;
  }
}

//-->
</script>
<style type="text/css">
<!--
INPUT {
background-color: #f2eadf;
color: #0d0d0d;
border: #0d0d0d 1px solid;
font-family: arial, verdana, ms sans serif;
font-weight: normal;
font-size: 12px;
text-align: center;
} 

TEXTAREA {
background-color: #f2eadf;
border: #0d0d0d 1px solid;
color: #0d0d0d;
font-family: arial, verdana, ms sans serif;
font-size: 12px;
font-weight: normal
} 

SELECT {
background-color: #f2eadf;
border: #0d0d0d 1px solid;
color: #0d0d0d;
font-family: arial, verdana, ms sans serif;
font-size: 12px;
font-weight: normal
} 

.radioStyle {
background-color: #ffffff;
font-family: verdana;
border: white 1px solid;
font-size: 10px;
color: #ffffff
}

DIV.Scroll {
	height: 135px;
	overflow: auto;
	width: 246;
}

-->
</style></head>
 

<body bgcolor="#f2eadf">

<form method="" action="" name="form2">

  <table width="600" cellspacing="0" cellpadding="0" border="0" bgcolor="#d6dcda">
    <tbody><tr valign="middle" bgcolor="#ebf2f2" align="center"> 
      <td colspan="3"> 
          
        <table width="100%" cellspacing="1" cellpadding="1" border="0" bgcolor="#ebf2f2">
          <tbody><tr align="center"> 
            <td> <font size="2" face="Arial, Helvetica, sans-serif" color="#0d0d0d"><b><font color="#0d0d0d">Calendar and Cosmology</font></b></font></td>
            </tr>
          </tbody></table>
    </td> 
</tr>
 <tr>
    <td width="3" height="3"><img src="images/TOP_L.gif" width="3" height="3"></td>
    <td bgcolor="#ebf2f2"></td>
    
  </tr>
  <tr>
      <td height="198" bgcolor="#ebf2f2"></td>
      <td valign="top" height="198"> 
        <table width="600" cellspacing="2" cellpadding="2" border="0">
          <tbody><tr> 
            <td colspan="3"> 
				
            <img width="592" height="440" border="0"></td>
          </tr>
          <tr> 
            <td width="200"><table cellspacing="1" cellpadding="0" border="0" bgcolor="#ebf2f2">
  <tbody><tr align="left"> 
    <td width="21" valign="middle"><img src="images/remote_x.jpg" width="16" height="16"></td>
    <td width="36" valign="middle"><font size="1" face="Arial, Helvetica, sans-serif">Remote</font></td>
    <td width="24" valign="middle"><img src="images/waxing_x.jpg" width="16" height="16"></td>
    <td width="31" valign="middle"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td>
    <td width="24" valign="middle"><img src="images/coterm_x.jpg" width="16" height="16"></td>
    <td width="53" valign="middle"><font size="1" face="Arial, Helvetica, sans-serif">Coterminous</font></td>
    <td width="24" valign="middle"><img src="images/waning_x.jpg" width="16" height="16"></td>
    <td width="31" valign="middle"><font size="1" face="Arial, Helvetica, sans-serif">Waning</font></td>
  </tr>
</tbody></table>
</td>
            <td width="250" align="center">
              <table cellspacing="0" cellpadding="0" border="0" align="right">
                <tbody><tr> 
                  <td></td>
                </tr>
              </tbody></table>
			</td>
            <td width="150" align="center"> 
              <select name="calendar" onchange="clickSetCalendar(value)">
                <option value="1" selected="">Galifar</option>
                <option value="2">Druid</option>
                <option value="3">Ancient Dwarven</option>
                <option value="4">Halfling</option>
                <option value="5">Generic</option>
              </select>
            </td>
          </tr>
        </tbody></table>
      </td>
      
  </tr>
  <tr>
    
    
    <td><img src="images/Bottom_R.gif" width="3" height="3"></td>
  </tr>
    <tr bgcolor="#ebf2f2" align="center"> 
      <td colspan="3">
        <table width="100%" cellspacing="1" cellpadding="1" border="0" bgcolor="#ebf2f2">
          <tbody>
        </tbody></table>
      </td> 
</tr>


</tbody></table>
  </form>





<div id="pagedisplay1" style="position: absolute; top: 55; left: 17; z-index: 2;"><form method="" action="" name="form1"><table width="178" cellspacing="2" cellpadding="2" border="0"><tbody><tr> <td width="26%" align="right"><b><font size="3" face="Arial, Helvetica, sans-serif">Year</font></b></td><td width="74%"> <input type="text" name="year" size="5" maxlength="8" value="998" onchange="clickSetYear(value)"><font size="1" face="Arial, Helvetica, sans-serif">YK </font></td></tr><tr> <td width="26%" align="right"><b><font size="3" face="Arial, Helvetica, sans-serif">Month</font></b></td><td width="74%"> <select name="month" onchange="clickSetMonth(value)"><option value="1" selected="">Zarantyr</option><option value="2">Olarune</option><option value="3">Therendor</option><option value="4">Eyre</option><option value="5">Dravago</option><option value="6">Nymm</option><option value="7">Lharvion</option><option value="8">Barrakas</option><option value="9">Rhaan</option><option value="10">Sypheros</option><option value="11">Aryth</option><option value="12">Vult</option></select></td></tr><tr> <td width="26%" align="right"><b><font size="3" face="Arial, Helvetica, sans-serif">Day</font></b></td><td width="74%"> <select name="day" onchange="clickSetDay(value)"><option value="1" selected="">1</option><option value="2">2</option><option value="3">3</option><option value="4">4</option><option value="5">5</option><option value="6">6</option><option value="7">7</option><option value="8">8</option><option value="9">9</option><option value="10">10</option><option value="11">11</option><option value="12">12</option><option value="13">13</option><option value="14">14</option><option value="15">15</option><option value="16">16</option><option value="17">17</option><option value="18">18</option><option value="19">19</option><option value="20">20</option><option value="21">21</option><option value="22">22</option><option value="23">23</option><option value="24">24</option><option value="25">25</option><option value="26">26</option><option value="27">27</option><option value="28">28</option></select></td></tr><tr> <td colspan="2" width="100%" align="center"><img src="https://user-images.githubusercontent.com/39757078/123530276-a0322e80-d6b5-11eb-8247-16e9563b646c.png"></td></tr></tbody></table></form></div>
<div id="pagedisplay2" style="position: absolute; top: 42; left: 202; z-index: 2;"><table width="250" cellspacing="2" cellpadding="0" border="0" bgcolor="#CCCCCC"><tbody><tr bgcolor="#FFFFFF"> <td width="232"> <div class="Scroll"><table width="100%" cellspacing="1" cellpadding="1" border="0" bgcolor="#FFFFFF"><tbody><tr valign="top" align="left"> </tr></tbody></table></div></td></tr></tbody></table></div>
<div id="pagedisplay3" style="position: absolute; top: 42; left: 459; z-index: 2;"><table width="150" cellspacing="2" cellpadding="2" border="0" bgcolor="#CCCCCC"><tbody><tr> <td colspan="7" bgcolor="#E6E6E6"> <div align="center"><b><font size="2" face="Arial, Helvetica, sans-serif">Zarantyr&nbsp;&nbsp;&nbsp;998<font size="1"> YK</font></font></b></div></td></tr><tr> <td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">S</font></div></td><td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">M</font></div></td><td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">Z</font></div></td><td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">W</font></div></td><td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">Z</font></div></td><td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">F</font></div></td><td bgcolor="#FFFFB7"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">S</font></div></td></tr><tr> <td style="background-color: rgb(215, 249, 200);" onclick="javascript:clickChangeDay(1)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#d7f9c8'" bgcolor="#d7f9c8"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">1</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(2)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">2</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(3)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">3</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(4)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">4</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(5)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">5</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(6)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">6</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(7)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">7</font></div></td></tr><tr> <td style="cursor:hand" onclick="javascript:clickChangeDay(8)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">8</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(9)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">9</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(10)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">10</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(11)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">11</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(12)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">12</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(13)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">13</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(14)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">14</font></div></td></tr><tr> <td style="cursor:hand" onclick="javascript:clickChangeDay(15)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">15</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(16)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">16</font></div></td><td style="background-color: rgb(255, 255, 255);" onclick="javascript:clickChangeDay(17)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">17</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(18)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">18</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(19)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">19</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(20)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">20</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(21)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">21</font></div></td></tr><tr> <td style="cursor:hand" onclick="javascript:clickChangeDay(22)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">22</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(23)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">23</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(24)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">24</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(25)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">25</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(26)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">26</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(27)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">27</font></div></td><td style="cursor:hand" onclick="javascript:clickChangeDay(28)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#ffffff'" bgcolor="#ffffff"> <div align="center"><font size="1" face="Arial, Helvetica, sans-serif">28</font></div></td></tr><tr> <td colspan="7" bgcolor="#E6E6E6" align="center"> <font size="1"><a href="javascript:clickMonthBack()"><img src="images/month_l.jpg" alt="Back 1 Month" border="0"></a><img src="images/grey_dot3.jpg" width="7" height="5"><a href="javascript:clickMonthForward()"><img src="images/month_r.jpg" alt="Forward 1 Month" border="0"></a><img src="images/grey_dot3.jpg" width="64" height="5"><a href="javascript:showMonthPhases()"><img src="images/tiny_moon.jpg" alt="Moon Phases This Month" border="0"></a><img src="images/grey_dot3.jpg" width="7" height="5"><a href="javascript:showPrintMonth()"><img src="images/month_icon.jpg" alt="Printer Friendly Calendar" border="0"></a></font></td></tr></tbody></table></div>
<div id="pagedisplay4" style="position: absolute; top: 188; left: 17; z-index: 2;"><table width="435" cellspacing="1" cellpadding="0" border="0" bgcolor="#CCCCCC"><tbody><tr> <td> <table width="100%" cellspacing="1" cellpadding="1" border="0" bgcolor="#CCCCCC"><tbody><tr> <td width="59" bgcolor="#E6E6E6" align="center"><b><font size="2" face="Arial, Helvetica, sans-serif">Plane</font></b></td><td width="50" bgcolor="#E6E6E6" align="center"><b><font size="2" face="Arial, Helvetica, sans-serif">Status</font></b><font size="1" color="#CCCCCC">-</font></td><td width="216" bgcolor="#E6E6E6" align="center"><font size="2" face="Arial, Helvetica, sans-serif" color="#FFFFFF"><img src="images/grey_dot3.jpg" width="1" height="5"></font></td><td width="134" bgcolor="#E6E6E6" align="center"><font size="2" face="Arial, Helvetica, sans-serif" color="#FFFFFF"><img src="images/grey_dot3.jpg" width="134" height="5"></font></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(1)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Daanvi</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;16801 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(2)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Dal Quor</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif"><font color="#a600a6">Remote</font></font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;No Information Available</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(3)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Dolurrh</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;8242 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(4)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Fernia</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif"><font color="#a5a5a5">Waning</font></font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;337 days until Remote.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(5)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Irian</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;85 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(6)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Kythri</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif"><font color="#008c00">Coterm.</font></font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;1266 days until Waning.&nbsp;*</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(7)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Lamannia</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;89 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(8)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Mabar</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;419 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(9)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Risia</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;336 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(10)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Shavarath</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;2017 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(11)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Syrania</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;840 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(12)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Thelanis</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;17725 days until Coterminous.</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr><tr> <td style="cursor:hand" onclick="javascript:showPlaneInfo(13)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" bgcolor="#FFFFFF" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Xoriat</font></td><td bgcolor="#FFFFFF" align="center"><font size="1" face="Arial, Helvetica, sans-serif">Waxing</font></td><td bgcolor="#FFFFFF" align="left"><font size="1" face="Arial, Helvetica, sans-serif">&nbsp;587833 days until Coterminous.&nbsp;**</font></td><td bgcolor="#FFFFFF" align="center"><img src="images/bar_L_end.jpg" width="7" height="18"><img src="images/bar_purple.jpg" width="10" height="18"><img src="images/bar_White.jpg" width="100" height="18"><img src="images/bar_green.jpg" width="10" height="18"><img src="images/bar_R_end.jpg" width="7" height="18"></td></tr></tbody></table></td></tr></tbody></table></div>
<div id="pagedisplay5" style="position: absolute; top: 188; left: 459; z-index: 2;"><table width="150" cellspacing="0" cellpadding="1" border="0" bgcolor="#CCCCCC"><tbody><tr> <td> <table width="100%" cellspacing="1" cellpadding="1" border="0" bgcolor="#CCCCCC"><tbody><tr> <td width="57%" bgcolor="#E6E6E6" align="center"><b><font size="2" face="Arial, Helvetica, sans-serif">Moon</font></b></td><td width="43%" bgcolor="#E6E6E6" align="center"><b><font size="2" face="Arial, Helvetica, sans-serif">Phase</font></b></td></tr><tr bgcolor="#FFFFFF"> <td style="background-color: rgb(255, 255, 255);" onclick="javascript:showMoonPhases(1)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Nymm</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(2)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Sypheros</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(3)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Therendor</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(4)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Rhaan</font></td><td width="43%" align="center"><img src="images/Moon_8.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(5)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Olarune</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(6)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Eyre</font></td><td width="43%" align="center"><img src="images/Moon_6x.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(7)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Vult</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(8)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Zarantyr</font></td><td width="43%" align="center"><img src="images/Moon_6x.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(9)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Aryth</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(10)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Dravago</font></td><td width="43%" align="center"><img src="images/Moon_4.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(11)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Lharvion</font></td><td width="43%" align="center"><img src="images/Moon_4.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td style="cursor:hand" onclick="javascript:showMoonPhases(12)" onmouseover="this.style.backgroundColor='#ffb0ff'" onmouseout="this.style.backgroundColor='#FFFFFF'" width="57%" align="left"><font size="2" face="Arial, Helvetica, sans-serif">Barrakas</font></td><td width="43%" align="center"><img src="images/Moon_1.jpg" width="18" height="18"></td></tr><tr bgcolor="#FFFFFF"> <td width="57%" bgcolor="#E6E6E6" align="left"><font size="2" face="Arial, Helvetica, sans-serif" color="#FFFFFF"><img src="images/grey_dot3.jpg" width="13" height="18"></font></td><td width="43%" height="18" bgcolor="#E6E6E6" align="center"><font size="2" face="Arial, Helvetica, sans-serif" color="#FFFFFF"><img src="images/grey_dot3.jpg" width="13" height="18"></font></td></tr></tbody></table></td></tr></tbody></table></div>
<div id="planedisplay1" style="position: absolute; top: 210px; left: 377px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay2" style="position: absolute; top: 231; left: 327; z-index: 3;"><img src="images/bar_Pointer_P.gif"></div>
<div id="planedisplay3" style="position: absolute; top: 252px; left: 376px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay4" style="position: absolute; top: 273px; left: 368px; z-index: 3;"><img src="images/bar_Pointer_Grey.gif"></div>
<div id="planedisplay5" style="position: absolute; top: 294px; left: 409px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay6" style="position: absolute; top: 315px; left: 427px; z-index: 3;"><img src="images/bar_Pointer_G.gif"></div>
<div id="planedisplay7" style="position: absolute; top: 336px; left: 376px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay8" style="position: absolute; top: 357px; left: 377px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay9" style="position: absolute; top: 378px; left: 385px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay10" style="position: absolute; top: 399px; left: 391px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay11" style="position: absolute; top: 420px; left: 377px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay12" style="position: absolute; top: 441px; left: 377px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="planedisplay13" style="position: absolute; top: 462px; left: 377px; z-index: 3;"><img src="images/bar_Pointer.gif"></div>
<div id="pagedisplay6" style="position: absolute; top: 492; left: 328; z-index: 3;"><a href="javascript:clickStartSkipBack()"><img src="images/skip_b1.jpg" alt="Year Back" width="18" height="18" border="0"></a><font size="2" face="Arial, Helvetica, sans-serif" color="#FFFFFF"><img src="images/white.jpg" width="5" height="18"><a href="javascript:clickStartReverse()"><img src="images/reverse1.jpg" alt="Automated Back 1 Day" width="18" height="18" border="0"></a><img src="images/white.jpg" width="5" height="18"><a href="javascript:clickStop()"><img src="images/stop1.jpg" alt="Stop Automation" width="18" height="18" border="0"></a><img src="images/white.jpg" width="5" height="18"><a href="javascript:clickStartAuto()"><img src="images/start1.jpg" alt="Automated Forward 1 Day" width="18" height="18" border="0"></a><img src="images/white.jpg" width="5" height="18"><a href="javascript:clickStartSkipForward()"><img src="images/skip_f1.jpg" alt="Year Forward" width="18" height="18" border="0"></a><img src="images/white.jpg" width="17" height="18"></font></div>
<div id="speeddisplay" style="position: absolute; top: 495; left: 444; z-index: 3;"></div>
<div id="speeddisplay2" style="position: absolute; top: 495; left: 315; z-index: 3;"></div>
<script>
showPart1();
showPart2(sText);
showPart3();
showPart5();
showPart6(1);
movePlanes();
showPlanes();
showPart4();
</script>
</body>
