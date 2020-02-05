# Dicom Data Source for Apache Spark

A library for reading the dicom images as a `spark SQL` data frame.


## Linking 

This library is cross-published for `scala 2.11` and `java 1.8.0_221`.The third party library named
`dcm-4che` source code was also used for developing the library.
 
You can link against this library in your program at the following coordinates:


#### Using Maven:
```
<dependency>
    <groupId>com.abzoobabd</groupId>
    <artifactId>spark-dicom</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```


#### With `spark-shell` or `spark-submit`

This library can also be added to spark jobs launched through `spark-shell` or `spark-submit` by using the `--packages`
command line option. For example,to include it when starting the spark shell:
    `$bin/spark-shell --packages com.abzoobabd:spark-dicom:1.0-SNAPSHOT`
    
Unlike using `--jars`,using `--packages` ensures that this library and its dependencies will be added to the classpath.
The `--packages` argument can also be used with `bin/spark-submit`.


## Features

Dicom Data Source for Spark supports reading the dicom images in the `Spark SQL` data frame.It also returns the seperate 
data frame containing the details regarding the corrupt files.

`Schema`  of the data frame containing the dicom data is as follows:

It contains three columns named `origin`,`metadata` and `pixeldata`.

1. `origin` contains the file path of dicom file.
2. `metadata` contains the patient metadata.
3. `pixeldata` contains the pixel data as array of bytes.

`Schema` of the data frame containing the corrupt data is as follows:

It contains two columns named `origin`,`exception`.

1. `origin` contains the file path of the dicom file.
2. `exception` conatins the message displaying the exception occured while reading the dicom file.


## Code Snippets 


#### Scala API.

```scala

//import the package

import dicomread
import java.io.{ByteArrayInputStream,File}
import javax.imageio.ImageIO

//read the dicom files from hadoop file system or local filesystem
//dcmdf is the data frame containing the dicom files data.
//cdf is the corrupt data frame containing the information about corrupt file.
val (dcmdf,cdf) = dicomread.readDicom(path,sparksession,numpartitions)

//retrieve a particular row froma a data frame.
val row = dcmdf.rdd.take(1).last

//retrieve metadata which is stored as json string in a dataframe.
//json string can be converted to the json object and can be further processed using appropriate library.
val jsonString = row(1).asInstance[String]

//retrieve the pixeldata and convert it into the jpg format or some other format.
val imgByteArray = row(2).asInstanceOf[Array[Byte]]
val bis = new ByteArrayInputStream(imgByteArray)
val bimage = ImageIO.read(bis)

val width = bimage.getWidth
val height = bimage.getHeight

ImageIO.write(bimage,"jpg",new File("abc.jpg"))
```


## Building from Source

This library is built with Maven.To build a JAR file simply run `mvn package` command from the project root.




