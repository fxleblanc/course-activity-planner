This project is affiliated with the [Maison du logiciel libre (ML<sup>2</sup>)](https://maisonlogiciellibre.org/) at <img src="http://www.etsmtl.ca/ETS/media/Prive/logo/ETS-rouge-ecran-fond_transparent.png" alt="ETS" width="64">.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [course-activity-planner](#course-activity-planner)
  - [How to use](#how-to-use)
    - [General principle](#general-principle)
    - [Start/End of activities](#startend-of-activities)
    - [Relative date or time modifiers](#relative-date-or-time-modifiers)
    - [Absolute time modifier](#absolute-time-modifier)
  - [Setup](#setup)
    - [Run unit tests](#run-unit-tests)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# course-activity-planner
![Build status](https://travis-ci.org/jdupl/course-activity-planner.svg?branch=master)
[![Coverage Status](https://coveralls.io/repos/jdupl/course-activity-planner/badge.svg?branch=master&service=github)](https://coveralls.io/github/jdupl/course-activity-planner?branch=master)


Tool for instructors to plan course activities and synchronize the data with syllabus, LMS, etc.

Moodle courses can be cloned and updated with new activity dates from a calendar. [Why?](https://github.com/fuhrmanator/course-activity-planner/blob/master/ooad/overview.md)


## How to use

### General principle

Quizzes (more to come) can be planned relative to Seminars and Practicas. Each activity adapts it's start and end dates with the calendar of specific dates.

`<activity to plan> <start at activity> <end at activity>`

Ex: `Quiz 1 is opened on Seminar 1 and closed right before Practica 2` would be possible with this line: `Q1 S1 P2`

* `Q1` stands for Quiz 1
* `S1` stands for Seminar 1
* `P2` stands for Practica 2

### Start/End of activities

Adding `F` to an activity will read the finishing time of the activity. Adding nothing or `S` will read the start time.

Ex: `Quiz 1 is opened right after Seminar 1 and closed right after Practica 1` would be `Q1 S1F P1F`


### Relative date or time modifiers

Amounts of time can be subtracted or added to activities.

Supports `+` or `-` combined with

* minutes: `m`
* hours: `h`
* days: `d`
* weeks: `w`

Ex: `1 hour after Seminar 1` would be `S1+1h`.

Ex: `15 minutes before Practica 2` would be `P2-15m`.

Ex: `Quiz 1 is opened 1 hour after Seminar 1 and closed 15 minutes before Practica 2` would be `Q1 S1+1h P2-15m`


### Absolute time modifier

The exact hours can be set to an activity.

Ex: `the day of Seminar 1 at 23:55` would be `S1@23:55`.

This can be used along with relative date or time modifiers.

Ex: `the day before Seminar 1 at 23:55` would be `S1-1d@23:55`.

**Please Note** when used with a relative modifier, the time modifier must be last.

`S1-1d@23:55` is valid

`S1@23:55-1d` is invalid

## Setup back-end only
* Setup a python virtualenv
```
cd python && virtualenv-3.4 env
```
* Activate the python virtualenv
```
. env/bin/activate
```
* Install pip dependencies
```
pip install -r requirements.txt
```
* Run it
```
./course_activity_planner.py
```

# Setup front-end
* Setup and run back-end
* Install bower dependencies
```
cd .. && bower install
```


### Run unit tests
* Run the test suite
```
nosetests
```
* Optionally, you can get a coverage report
```
nosetests --with-coverage
```

### Run the linter
```
pep8 && flake8
```
