# ELPI

[ELPI Preview App](https://docs.google.com/forms/d/e/1FAIpQLSeU8RO8n9iq84S5T3gZsjfxLF1nxKOEbSo8JZjI1rHHCQgXyw/viewform)

## Summary
This is a demo of an app that outputs an English Learners Progress Indicator score.  The link above is to a form that accepts 2 csv files as input and an email address.  There are 2 files in this repo that contain dummy data that can be uploaded to the form.  The email address should be a Gmail address so that results can be shared in the form of a Google Sheet.

## Background

### California School Dasbhoard

California's accountability system is based on a multiple measures system that assess how local educational agencies (LEAs) and schools are meeting the needs of their students. Performance on these measures is reported through the California School Dashboard (Dashboard). 

State measures include chronic absenteeism, graduation rate, suspension rate, English learner progress, and academic performance (which includes English language arts/literacy and mathematics). Future state measures will include performance on the California Science Test.

Based on performance on state and local measures, schools and districts may be identified for support to improve student outcomes.

### English Learners Progress Indicator (ELPI)

The ELPI is based on the English Language Proficiency Assessments for California (ELPAC). Several districts were interested in seeing what their ELPI score was as soon as they received their ELPAC scores, rather than wait several more weeks for their ELPI to be releasee on the CA Dasbhoard.  Data professionals from two of these districts put together a Google Sheet to calculate the ELPI score and wished to share it with the other school districts in Sonoma County.

While the Google Sheet was successful and the business logic relatively straightforward, the formulas ended up labyrinthine and difficult to troubleshoot.  Additionaly there was a lot of data cleanup and prep needed on the ELPAC files once they were copied into the sheet.

When I was asked to support the Sheet, I suggested leveraging Google Cloup Platform (GCP) to make a more maintainable app and thus this project was born.

## Overview

A Google Form acts as the front end to the app and it's only inputs are the current year ELPAC score file, the past year ELPAC score file, and the recipient email address to share the results with (the results are not emailed.  They are in a Google Sheet that is shared with the given email address).

Once the form is submitted, an Apps Script attached to the form calls a Google Cloud function using an HTTP trigger to upload the 2 files from a Drive folder to a Google Cloud Storage bucket. Once the 2 files are loaded, another function is called using an event trigger to load the files into BigQuery as tables.  Another function is then triggered to materialize a view that applies the business logic to calculate the ELPI score for each student.  One final function is triggered to write these results to a Google Sheet and share that sheet with the email address supplied in the form. 
