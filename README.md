# ELPI

# Background

## California School Dasbhoard

California's accountability system is based on a multiple measures system that assess how local educational agencies (LEAs) and schools are meeting the needs of their students. Performance on these measures is reported through the California School Dashboard (Dashboard). 

State measures include chronic absenteeism, graduation rate, suspension rate, English learner progress, and academic performance (which includes English language arts/literacy and mathematics). Future state measures will include performance on the California Science Test.

Based on performance on state and local measures, schools and districts may be identified for support to improve student outcomes.

## English Learners Progress Indicator (ELPI)

The ELPI is based on the English Language Proficiency Assessments for California (ELPAC). Several districts were interested in seeing what their ELPI score was as soon as they received their ELPAC scores, rather than wait several more weeks for their ELPI to be releasee on the CA Dasbhoard.  Data professionals from two of these districts put together a Google Sheet to calculate the ELPI score and wished to share it with the other school districts in Sonoma County.

While the Google Sheet was successful and the business logic relatively straightforward, the formulas ended up labyrinthine and difficult to troubleshoot.  Additionaly there was a lot of data cleanup and prep needed on the ELPAC files once they were copied into the sheet.

When I was asked to support the Sheet, I suggested leveraging Google Cloup Platform (GCP) to make a more maintainable app and thus this project was born.
