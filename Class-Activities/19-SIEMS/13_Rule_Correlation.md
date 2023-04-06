## Activity File: Rule Correlation


As the SOC manager at OMP, you have successfully normalized the various web server logs.

- Your manager would like you to make a plan for identifying an attack when it is occurring.

- Since you don't have a SIEM tool yet, your first task is to design a plainly-worded outline of a correlation rule that will be used to identify an attack.

- Your correlation rule will later be translated to real code that will create alerts on your SIEM.



### Instructions

Without using any code, design a rule that will assist with detecting the following security events:

1. There was suspicious and unsuccessful web activity from Beijing.
`if iplocation = Beijing, 
   and >5 failures in 5mins; 
   then alert SOC team
   if >50 failures in 1hr;
   then notify SOC manager`
   
2. There were floods of web requests from a single source IP in a short period of time.
`if ipaddress requests >120 per minute;
   then alert SOC team
   if >1000 in 10mins;
   then notify SOC manager`
   
3. There were suspicious successful web requests to access JPG images from IPs outside of the United States.
`if file request = .jpg
   and iplocation !=United States
   and >120 requests per min
   then alert SOC team
      if >500 in 5mins;
      then notify SOC manager`
---
