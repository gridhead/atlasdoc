# Pignus Agent for Internet Protection 
**Version 0.05**  
A Python GUI application for scanning URLs and domains for safety 

[Find the repository here](https://github.com/t0xic0der/pignus-agent-for-internet-protection)

<p align="center">
    <img src="https://img.shields.io/github/issues/t0xic0der/pignus-agent-for-internet-protection?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/forks/t0xic0der/pignus-agent-for-internet-protection?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/stars/t0xic0der/pignus-agent-for-internet-protection?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/license/t0xic0der/pignus-agent-for-internet-protection?style=flat-square&logo=appveyor&color=teal">
</p>

## Usage 
1.  Install and upgrade **virtualenv** if not already done by executing ```pip3 install virtualenv --user```
2.  Clone the repository on your local drive and make it your current working directory.
3.  Create a virtual environment by executing ```virtualenv venv```
4.  Activate the virtual environment by executing ```source venv/bin/activate```
5.  Install all dependencies for the project by executing ```pip3 install -r requirements.txt```
6.  Run the project by executing ```python3 pigipgui.py```
7.  Sign up at VirusTotal website to get your own public API key.
8.  Create a new file called `virustotal.key` and store your key there.
9.  Queue URL scanning, get URL report or get domain report of your target.
10. When done tinkering, deactivate the virtual environment by executing ```deactivate```
11. Give stars to the repository if it was helpful

## To-do
- **`COMPLETED!`** Build GUI and prototype UX for loopholes
- **`COMPLETED!`** Add function on single URLs for URL scanning
- **`COMPLETED!`** Add function on single URLs for URL reports
- **`COMPLETED!`** Add function on single URLs for domain reports
- **`COMPLETED!`** Add timer function to note the duration for scanning
- **`COMPLETED!`** Implement table iteration for list-of-tuples
- **`COMPLETED!`** Add clear button for all line edit boxes
- **`INCOMPLETE`** Add fixes for unresolved API request errors
- **`INCOMPLETE`** Cleanup and optimise code base
- **`INCOMPLETE`** Make miscellaneous bug fixes

## Changelog

### v0.01
1. Initial build
2. Built a robust GUI and checked loopholes
3. Added functionality to queue URL scan
4. Added way of dealing with APIKEY externally

### v0.02
1. Resolved API request errors from queue URL scan
2. Added timer function for queue URL scan
3. Handled exception where URLs could not be found
4. Handled exception where API key was not provided
5. Handled exception where API was overused

### v0.03
1. Added warning messages
2. Added functionality to get URL report
3. Switched fontface to improve legibility
4. Added clear button for all line edit boxes
5. Added message for timing and scan success

### v0.04
1. Resolved API request errors for get URL report
2. Added functionality to get domain report
3. Implemented table iterations for list-of-tuples
4. Fix for URLs which are blocked by the ISPs
5. Fix for timeout errors

### v0.05 (Current)
1. Cleaned up code from debug messages
2. Added a new set of fonts for rastering
3. Restructured `requirements.txt` for distribution
4. Added generic fix for unindexed errors
5. Fix for IndexError on table structuring

### v0.06 (Oncoming)
_To be decided_

## Screenshots

### Queue URL scanning (Basic layout, v0.05 onwards)
![Queue URL scanning (Basic layout, v0.05 onwards)](pics/apps/pgaip/ssurlsca.png)

### Queue URL scanning (Results from `t0xic0der.netlify.app`, v0.05 onwards)
![Queue URL scanning (Results from `t0xic0der.netlify.app`, v0.05 onwards)](pics/apps/pgaip/rpurlsca.png)

### Get URL report (Basic layout, v0.05 onwards)
![Get URL report (Basic layout, v0.05 onwards)](pics/apps/pgaip/ssurlrep.png)

### Get URL report (Results from `t0xic0der.netlify.app`, v0.05 onwards)
![Get URL report (Results from `t0xic0der.netlify.app`, v0.05 onwards)](pics/apps/pgaip/rpurlrep.png)

### Get domain report (Basic layout, v0.05 onwards)
![Get domain report (Basic layout, v0.05 onwards)](pics/apps/pgaip/ssdomrep.png)

### Get domain report (Results from `t0xic0der.netlify.app`, v0.05 onwards)
![Get domain report (Results from `t0xic0der.netlify.app`, v0.05 onwards)](pics/apps/pgaip/rpdomrep.png)

## Bugs
1. Some domains cannot be scanned due to ISP blockage or denial from the API provider.
2. Populating tables with data might take some time on single-core PCs.
3. Random API errors might occur some time - Try another URL first.

## Contribute
Fork, add, build and make a PR. You know the drill.
