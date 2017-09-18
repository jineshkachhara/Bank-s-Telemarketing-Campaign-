/*copying the data into work directory*/
proc copy in= project out=work;
select bank;
run;

/*getting the count of number of responders in the dataset*/
proc sql;
select distinct y,
count(y) as responders
from Bank
group by 1;
quit;

/*Data preparation: creating a new column/variable for each category of the variable*/
data bank_data1;
set bank;

length age_new $10. duration_new $10. campaign_new $5. previous_new $3.;

if 17<=age<=25 then age_new="18_25"; 
else if 26<=age<=35 then age_new="26_35"; 
else if 36<=age<=45 then age_new="36_45"; 
else if 46<=age<=55 then age_new="46_55"; 
else if 56<=age<=65 then age_new="56_65";  
else if 66<=age then age_new="66+";

if 0<=duration<=120 then duration_new="0-2mins";
else if 121<=duration<=240 then duration_new="3-4mins";
else if 241<=duration<=360 then duration_new="5-6mins";
else if 361<=duration<=480 then duration_new="7-8mins";
else if 481<=duration<=600 then duration_new="9-10mins";
else if 600<duration then duration_new="10+mins";

if campaign=1 then campaign_new="1";
else if campaign=2 then campaign_new="2";
else if campaign=3 then campaign_new="3";
else if campaign>3 then campaign_new="4+";

if previous=0 then previous_new="0";
else if previous=1 then previous_new="1";
else if previous>=1 then previous_new="2+";
run;

/*Converting the data into 0's and 1's and keeping the columns needed for further analysis */ 
data temp1;
set bank_data1;

if age_new='18_25' then age_18_25=1;
else age_18_25=0;
if age_new='26_35' then age_26_35=1;
else age_26_35=0;
if age_new='36_45' then age_36_45=1;
else age_36_45=0;
if age_new='46_55' then age_46_55=1;
else age_46_55=0;
if age_new='56_65' then age_56_65=1;
else age_56_65=0;
if age_new='66+' then age_66_above=1;
else age_66_above=0;

if duration_new="0-2mins" then duration_0_2=1;
else duration_0_2=0;
if duration_new="3-4mins" then duration_3_4=1;
else duration_3_4=0;
if duration_new="5-6mins" then duration_5_6=1;
else duration_5_6=0;
if duration_new="7-8mins" then duration_7_8=1;
else duration_7_8=0;
if duration_new="9-10mins" then duration_9_10=1;
else duration_9_10=0;
if duration_new="10+mins" then duration_11_above=1;
else duration_11_above=0;

if campaign_new='1' then campaign_1=1;
else campaign_1=0;
if campaign_new='2' then campaign_2=1;
else campaign_2=0;
if campaign_new='3' then campaign_3=1;
else campaign_3=0;
if campaign_new not in ('1','2','3') then campaign_4_above=1;
else campaign_4_above=0;

if previous_new='0' then previous_0=1;
else previous_0=0;
if previous_new='1' then previous_1=1;
else previous_1=0;
if previous_new='2+' then previous_2_above=1;
else previous_2_above=0;

if job='admin.' then job_admin=1;
else job_admin=0;
if job='blue-collar' then job_blue_collar=1;
else job_blue_collar=0;
if job='entrepreneu' then job_entrepreneu=1;
else job_entrepreneu=0;
if job='housemaid.' then job_housemaid=1;
else job_housemaid=0;
if job='management' then job_management=1;
else job_management=0;
if job='retired' then job_retired=1;
else job_retired=0;
if job='self-employ' then job_self_employ=1;
else job_self_employ=0;
if job='services' then job_services=1;
else job_services=0;
if job='student' then job_student=1;
else job_student=0;
if job='technician' then job_technician=1;
else job_technician=0;
if job='unemployed' then job_unemployed=1;
else job_unemployed=0;
if job='unknown' then job_unknown=1;
else job_unknown=0;

if marital='single' then marital_single=1;
else marital_single=0;
if marital='married' then marital_married=1;
else marital_married=0;
if marital='divorced' then marital_divorced=1;
else marital_divorced=0;
if marital='unknown' then marital_unknown=1;
else marital_unknown=0;

if Education='basic.4y' then Education_basic_4y=1;
else Education_basic_4y=0;
if Education='basic.6y' then Education_basic_6y=1;
else Education_basic_6y=0;
if Education='basic.9y' then Education_basic_9y=1;
else Education_basic_9y=0;
if Education='high.school' then Education_high_school=1;
else Education_high_school=0;
if Education='illiterate' then Education_illiterate=1;
else Education_illiterate=0;
if Education='professional.course' then Education_prof_course=1;
else Education_prof_course=0;
if Education='university.degree' then Education_univ_degree=1;
else Education_univ_degree=0;
if Education='unknown' then Education_unknown=1;
else Education_unknown=0;

if default='no' then default_no=1;
else default_no=0;
if default='yes' then default_yes=1;
else default_yes=0;
if default='unknown' then default_unknown=1;
else default_unknown=0;

if housing='no' then housing_no=1;
else housing_no=0;
if housing='yes' then housing_yes=1;
else housing_yes=0;
if housing='unk' then housing_unknown=1;
else housing_unknown=0;

if loan='no' then loan_no=1;
else loan_no=0;
if loan='yes' then loan_yes=1;
else loan_yes=0;
if loan='unk' then loan_unknown=1;
else loan_unknown=0;

if contact='cellular' then contact_cellular=1;
else contact_cellular=0;
if contact='telephone' then contact_telephone=1;
else contact_telephone=0;

if day_of_week='mon' then day_of_week_mon=1;
else day_of_week_mon=0;
if day_of_week='tue' then day_of_week_tue=1;
else day_of_week_tue=0;
if day_of_week='wed' then day_of_week_wed=1;
else day_of_week_wed=0;
if day_of_week='thu' then day_of_week_thu=1;
else day_of_week_thu=0;
if day_of_week='fri' then day_of_week_fri=1;
else day_of_week_fri=0;

if month='mar' then month_mar=1;
else month_mar=0;
if month='apr' then month_apr=1;
else month_apr=0;
if month='may' then month_may=1;
else month_may=0;
if month='jun' then month_jun=1;
else month_jun=0;
if month='jul' then month_jul=1;
else month_jul=0;
if month='aug' then month_aug=1;
else month_aug=0;
if month='sep' then month_sep=1;
else month_sep=0;
if month='oct' then month_oct=1;
else month_oct=0;
if month='nov' then month_nov=1;
else month_nov=0;
if month='dec' then month_dec=1;
else month_dec=0;

if poutcome='failure' then poutcome_failure=1;
else poutcome_failure=0;
if poutcome='success' then poutcome_success=1;
else poutcome_success=0;
if poutcome='nonexistent' then poutcome_nonexistent=1;
else poutcome_nonexistent=0;

keep 
y
job_admin
job_blue_collar
job_entrepreneu
job_housemaid
job_management
job_retired
job_self_employ
job_services
job_student
job_technician
job_unemployed
job_unknown
marital_single
marital_married
marital_divorced
marital_unknown
Education_basic_4y
Education_basic_6y
Education_basic_9y
Education_high_school
Education_illiterate
Education_prof_course
Education_univ_degree
Education_unknown
default_no
default_yes
default_unknown
housing_no
housing_yes
housing_unknown
loan_no
loan_yes
loan_unknown
contact_cellular
contact_telephone
day_of_week_mon
day_of_week_tue
day_of_week_wed
day_of_week_thu
day_of_week_fri
month_mar
month_apr
month_may
month_jun
month_jul
month_aug
month_sep
month_oct
month_nov
month_dec
age_18_25
age_26_35
age_36_45
age_46_55
age_56_65
age_66_above
duration_0_2
duration_3_4
duration_5_6
duration_7_8
duration_9_10
duration_11_above
campaign_1
campaign_2
campaign_3
campaign_4_above
previous_0
previous_1
previous_2_above

poutcome_failure
poutcome_success
poutcome_nonexistent

emp_var_rate
cons_price_idx
cons_conf_idx
euribor3m
nr_employed;

label
job_admin = 'Admin '
job_blue_collar = 'Blue-collar Job'
job_entrepreneu = 'Entrepreneur Job'
job_housemaid = 'Housemaid Job'
job_management = 'Management Job'
job_retired = 'Retired Job'
job_self_employ = 'Self-employed Job'
job_services = 'Services Job'
job_student = 'Student Job'
job_technician= 'Technician Job'
job_unemployed = 'Unemployed Job'
job_unknown = 'Unknown Job'
marital_single = 'Single'
marital_married = 'Married'
marital_divorced = 'Divorced'
marital_unknown = 'Marital Status:Unknown'
Education_basic_4y = 'Education Basic 4years'
Education_basic_6y = 'Education Basic 6years'
Education_basic_9y = 'Education Basic 9years'
Education_high_school = 'Education High-school'
Education_illiterate = 'Education Illiterate'
Education_prof_course = 'Education Professional Course'
Education_univ_degree = 'Education University Degree'
Education_unknown = 'Education Unknown'
default_no = 'No credit in default'
default_yes = 'Has credit in default'
default_unknown = 'Unknwon Credit'
housing_no = 'No Housing Loan'
housing_yes = 'Has Housing Loan'
housing_unknown = 'Unknown Housing Loan'
loan_no = 'No Personal Loan'
loan_yes = 'Has Personal Loan'
loan_unknown = 'Unknown Personal Loan'
contact_cellular = 'Cellular Phone'
contact_telephone = 'Telephone'
day_of_week_mon = 'Monday - Last Contact day of the week'
day_of_week_tue = 'Tuesday - Last Contact day of the week'
day_of_week_wed = 'Wednesday - Last Contact day of the week'
day_of_week_thu = 'Thursday - Last Contact day of the week'
day_of_week_fri = 'Friday - Last Contact day of the week'
month_mar = 'March - Last contact month of the year'
month_apr = 'April - Last contact month of the year'
month_may = 'May - Last contact month of the year'
month_jun = 'June - Last contact month of the year'
month_jul = 'July - Last contact month of the year'
month_aug = 'August - Last contact month of the year'
month_sep = 'September - Last contact month of the year'
month_oct = 'October - Last contact month of the year'
month_nov = 'November - Last contact month of the year'
month_dec = 'December - Last contact month of the year'
age_18_25 = 'Age:18-25'
age_26_35 = 'Age:26-35'
age_36_45 = 'Age:36-45'
age_46_55 = 'Age:46-55'
age_56_65 = 'Age:56-65'
age_66_above = 'Age:66+'
duration_0_2 = 'Last call: 0-2mins'
duration_3_4 = 'Last call: 3-4mins'
duration_5_6 = 'Last call: 5-6mins'
duration_7_8 = 'Last call: 7-8mins'
duration_9_10 = 'Last call: 9-10mins'
duration_11_above = 'Last call: 10+mins'
campaign_1 = 'Contacts in this campaign:1'
campaign_2 = 'Contacts in this campaign:2'
campaign_3 = 'Contacts in this campaign:3'
campaign_4_above = 'Contacts in this campaign:4+'
previous_0 = 'Contacts in previous campaign:0'
previous_1 = 'Contacts in previous campaign:1'
previous_2_above = 'Contacts in previous campaign:2+'
poutcome_failure ='Previous Mktg campaign : Failure'
poutcome_success = 'Previous Mktg campaign : Success'
poutcome_nonexistent= 'Previous Mktg campaign : Nonexistent'

emp_var_rate='Employment variation rate - quarterly indicator'
cons_price_idx='Consumer price index - monthly indicator'
cons_conf_idx='Consumer confidence index - monthly indicator'
euribor3m='euribor 3 month rate - daily indicator'
nr_employed='Number of employees - quarterly indicator'
;
run;
/*Code to run logistic regression oin the dataset*/
PROC LOGISTIC DATA=TEMP1 DESC;
class job_admin	job_blue_collar	job_entrepreneu	job_housemaid	job_management	job_retired	job_self_employ	job_services	job_student	job_technician	job_unemployed	job_unknown	marital_single	marital_married	marital_divorced	marital_unknown	Education_basic_4y	Education_basic_6y	Education_basic_9y	Education_high_school	Education_illiterate	Education_prof_course	Education_univ_degree	Education_unknown	default_no	default_yes	default_unknown	housing_no	housing_yes	housing_unknown	loan_no	loan_yes	loan_unknown	contact_cellular	contact_telephone	day_of_week_mon	day_of_week_tue	day_of_week_wed	day_of_week_thu	day_of_week_fri	month_mar	month_apr	month_may	month_jun	month_jul	month_aug	month_sep	month_oct	month_nov	month_dec	age_18_25	age_26_35	age_36_45	age_46_55	age_56_65	age_66_above	duration_0_2	duration_3_4	duration_5_6	duration_7_8	duration_9_10	duration_11_above	campaign_1	campaign_2	campaign_3	campaign_4_above	previous_0	previous_1	previous_2_above	poutcome_failure	poutcome_success	poutcome_nonexistent;
MODEL y = job_admin	job_blue_collar	job_entrepreneu	job_housemaid	job_management	job_retired	job_self_employ	job_services	job_student	job_technician	job_unemployed	job_unknown	marital_single	marital_married	marital_divorced	marital_unknown	Education_basic_4y	Education_basic_6y	Education_basic_9y	Education_high_school	Education_illiterate	Education_prof_course	Education_univ_degree	Education_unknown	default_no	default_yes	default_unknown	housing_no	housing_yes	housing_unknown	loan_no	loan_yes	loan_unknown	contact_cellular	contact_telephone	day_of_week_mon	day_of_week_tue	day_of_week_wed	day_of_week_thu	day_of_week_fri	month_mar	month_apr	month_may	month_jun	month_jul	month_aug	month_sep	month_oct	month_nov	month_dec	age_18_25	age_26_35	age_36_45	age_46_55	age_56_65	age_66_above	duration_0_2	duration_3_4	duration_5_6	duration_7_8	duration_9_10	duration_11_above	campaign_1	campaign_2	campaign_3	campaign_4_above	previous_0	previous_1	previous_2_above	poutcome_failure	poutcome_success	poutcome_nonexistent	emp_var_rate	cons_price_idx	cons_conf_idx	euribor3m	nr_employed
/  SELECTION = STEPWISE; output out= result p = prob;
RUN;

/*converting the decision column i.e. whether responder or not into binary data*/
data project;
set temp11;
if y="ye" then output=1;
else output=0;
drop y;
run;

/*Checking for multi collinearity*/
proc reg data=project;
model output= duration_11_above	nr_employed	duration_9_10	duration_0_2	month_may	poutcome_success	duration_3_4	month_mar	emp_var_rate	duration_5_6	previous_0	month_apr	month_nov	job_blue_collar	euribor3m	age_36_45	default_no	month_sep	contact_cellular	cons_price_idx	month_aug	month_jun	campaign_2	age_46_55	day_of_week_mon	job_services	age_66_above	Education_univ_degree	age_18_25 / vif selection=stepwise;
run;
/*Checking for multi collinearity*/
proc reg data=project;
model output = duration_11_above	duration_9_10	poutcome_success	month_mar	previous_0	month_apr	month_nov	job_blue_collar	age_36_45	default_no	contact_cellular	month_aug	month_jun	campaign_2	age_46_55	day_of_week_mon	job_services	age_66_above	Education_univ_degree	age_18_25 / vif selection=stepwise;
run;
/*Running logistic regression on the important variables*/
proc logistic data=project desc;
model output= /*age_46_55 day_of_week_mon*/		/*month_nov*/	age_18_25 job_blue_collar month_jun month_apr	
default_no	contact_cellular	age_66_above	month_mar	poutcome_success day_of_week_mon	job_blue_collar
/ selection = stepwise; output out = final p=prob;
run;
/*Code to convert data into deciles*/
proc rank data=final out=scoring_rank descending groups=10;
var prob;
ranks prob;
run;
/*Getting the number of responders and non responders in the particular deciles*/
proc freq data=scoring_rank;
tables prob prob*output;
run;
/*Code to extract data into a csv files*/
proc export 
data=final
dbms=csv
outfile="C:\final_final.csv"
replace;
run;
