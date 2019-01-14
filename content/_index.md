---
title: ""
date: 2019-01-13T17:34:15-05:00
draft: false
---


<div style="width: 50%; margin: auto;"> <img src="/public/schedule.png" /></div>

Minervaclient provides a minimalist, composable command-line client, and Python API for Minerva, myCourses, and other tools, so you can focus on extracting information, creating workflows and building apps. Formatters allow you to export data to <a href="#">plain text</a>, <a href="#">JSON</a>, your <a href="#">calendar</a> or <a href="#">spreadsheet</a>. Minervaclient can <a href="#schedule">retrieve your course, assignment and final exam schedules</a>, <a href="#register">register and search for courses</a>, <a href="#assignments">submit assignments</a>, and can perform countless other tasks.


```shell
$ minervac register -tWINTER2019 COMP-527-001 PSYC-315-001
```
<b><a href="#">See another example&hellip;</a></b>

## Install
```shell
pip install minervaclient
```

Minervaclient uses <a href="#">requests</a> to access HTTP endpoints, <a href="#">beautifulsoup4</a> to extract data from webpages and <a href="#">keyring</a> to securely store your credentials using your operating system's keyring.

### Recent improvements
* Blah bleh
* Bleh blah
* EEk horse

## `register`

```shell
$ minervac register -tF16 COMP-273-001
```

`register` performs course registration, by course code (e.g. `CLAS-201-002`) or by CRN (e.g. `8144`). You must specify the term you are registering for,  via the `-t` option, but the term code format is very flexible.

### Options

 Option | Description
--------|------------------ 
 `-j`   | Jobs allow you to keep track of groups of courses you are registering for at the same time. Once you're enrolled in a class, it's removed from the job and registration will only be re-attempted for the remaining classes. 

### Supported formatters
* `text`


## `schedule`

```shell
$ minervac schedule -t201801
```

Accesses course, assignment and final exam schedules. You must specify the term for which to view the schedule, via the `-t` option.

### Sources
 Option | Description
--------|------------------ 
  | (Default) Course schedule from Minerva 
 `-E`   | Final exam schedules for registered courses 
 `-A`   | Assignment due dates from myCourses 
 
### Supported formatters
* `text`
* `calendar` (plain-text calendar)
* `html`, `pdf`, `png` (visual timetable)
* `ics` (vCalendar)
* `json`
* `csv` (spreadsheet)

## `search`

```shell
$ minervac search -t FALL2019 COMP-202
```

Searches the course schedule, with prerequisite and restriction information from the eCalendar integrated. More advanced queries can be performed via the [SQL](#) interface.

### Options
  Option | Description
--------|------------------ 
 `-L` | Lectures only 
 `-T` | Tutorials only 


### Supported formatters
* `text`
* `calendar` (plain-text calendar)
* `html`, `pdf`, `png` (visual timetable)
* `ics` (vCalendar)
* `json`
* `csv` (spreadsheet)

## `transcript`

```shell
$ minervac transcript
```

Accesses the unofficial transcript from Minerva, displaying all enrolled terms by default.

### Options
  Option | Description
--------|------------------ 
 Option | Description |
 `-t `*term* | Limit the displayed records to a given term 

### Supported formatters
* `text`
* `json`
* `csv`


## `grades`
```shell
$ minervac grades 327306
```

`grades` retrieves assignment and course grades from myCourses. Currently, you need to specify the myCourses OU (course code) to access class information.

### Supported formatters
* `text`
* `json`
* `csv`

## `assign`

```shell
$ minervac assign 327306 -A4
```

`assign` submits assignments and verifies submission status. Currently, you need to specify the myCourses OU (course code) to access class information.

## Formatters

Minervaclient supports a variety of output formatters, selected via the `-f` option. Most formatters are generic and can be used with any subcommand, but some commands offer specific ways to display information. If you're using the Python API, you can easily create a custom formatter as well.

 Name | Description 
-------|-------------
 `text` | Plain text, separated into columns. You can use `-c` to customize which columns to output 
 `json` | JSON for REST APIs or use with [jq](#) 
 `csv` | CSV for import into Microsoft Excel, Google Sheets and other spreadsheet software
 

## At your university

If your university uses Banner (google for your university name + "bwckgens.csv"), Shibboleth or Desire2Learn, you might be able to take advantage of `minervaclient`. Try editing the `base_urls` in `config.py` and let us know if how far you get.

## Warning

You are solely responsible for assessing whether your use of `minervac` is in compliance applicable McGill policies, including the [McGill Policy on the Responsible Use of IT Resources](http://www.mcgill.ca/secretariat/files/secretariat/responsible-use-of-mcgill-it-policy-on-the.pdf). Do not access McGill services with excessive frequency.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
