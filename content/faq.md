title=Frequently Asked Questions
date=2019-03-18
status=published
type=col8
~~~~~~

<h2 class='body-green text-color' >FAQ</h2>

### Header 

#### Q: Nextflow crashes when run on the cluster, what's wrong? Why is Nextflow using so much memory?
A: Nextflow by default will use whatever RAM settings the Java Virtual Machine (JVM) uses. On a need-basis Nextflow will thus use increasing amounts of memory. One can mitigate this by specifying the minimum (-Xms) and minimum (-Xmx) amounts of memory Nextflow gets to use like so: NXF_OPTS='-Xms512m -Xmx2G' nextflow run [etc] Nextflow should run just fine with these settings, it does not actually strictly require all the RAM.

#### Q: How do you get a value from a script into another process? How to get an output value from a python script within nextflow process?
A: Write the value to a file and then use that file as a value channel to the next process. Alternatively do this with stdout.

#### Q: How do I get rid of new line character when using splitText()? How to parse list of IDs with splitText (get rid of new line character)?
A: Instead use splitCSV() or do the following:
inputChannel.splitText().map{it -> it.trim()}
