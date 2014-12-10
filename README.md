Json Recorder
-------------------------------

Simple tool to record JSON input and output in the Grails tests.


Usage:
Use left shift to recorder object with the name of the fixture (e.g. the
domain class name) and the JSON which should be recorded.

```
JsonRecorder rec = JsonRecorder.create('test/js-fixtures/earlslist', 'item')   

void "obtain the list of items in json format"() { 
    when: 
    controller.index(10)  

    def result = rec << 'list' << controller.response.json  
    then: 
    result?.size() == 10 
    result[0].description =~ /Item #\d+/ 
}
```