# MNG-6877
The test project to reproduce the https://issues.apache.org/jira/browse/MNG-6877 issue

`mvn package` as well as `mvn install` - doesn't work on the first try.

to build this project for the first time you need to

1. run `mvn install` from the project root 
1. go to apt-processor
1. run `mvn install`

Only after that `mvn package` and `mvn install` will work.

Please check the file `generated.txt` in `apt\target\generated-sources\annotations`. It should contains text "test 01"

BUT! if you change the source of apt-processor e.g `wr.append("test 01");` -> `wr.append("test 02");` in `org.gwtproject.editor.processor.AptProcessor` and run `mvn clean package` the file apt\target\generated-sources\annotations\generated.txt still contains text "test 01", even if run `mvn clean install` the file apt\target\generated-sources\annotations\generated.txt still contains text "test 01". You need to run `mvn clean install` second time to correct regenerate the test file.
