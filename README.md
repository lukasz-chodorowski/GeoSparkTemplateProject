# GeoSpark Template Project
[![Build Status](https://travis-ci.org/jiayuasu/GeoSparkTemplateProject.svg?branch=master)](https://travis-ci.org/jiayuasu/GeoSparkTemplateProject)

This repository contains six template projects for GeoSpark, GeoSparkSQL and GeoSparkViz. The template projects have been configured properly. You are able to compile, package, and run the code locally without any extra coding.

GeoSpark repository is available here: [GeoSpark GitHub Repository](https://github.com/DataSystemsLab/GeoSpark)

The Master branch supports GeoSpark 1.0.0 and later. Old templates for GeoSpark (0.9.1 and earlier), Babylon (0.3 and earlier) are available here: [Old template](https://github.com/jiayuasu/GeoSparkTemplateProject/tree/old-template)

GeoSpark-Analysis is a template that shows how to use GeoSpark in Spatial Data Mining: [GeoSpark-Analysis](https://github.com/jiayuasu/GeoSparkTemplateProject/tree/master/geospark-analysis)

## Folder structure
The folder structure of this repository is as follows.

* geospark
  * scala: **GeoSpark Scala Template Project**
  * java: **GeoSpark Java Template Project**
* geospark-sql
  * scala: **GeoSparkSQL Scala Template Project**. Java project uses the exactly same SQL APIs.
* geospark-viz
  * scala: **GeoSparkViz Scala Template Project**
  * java: **GeoSparkViz Java Template Project**
* geospark-analysis: **GeoSpark spatial data mining project**
  * Spatial Co-location Pattern Mining: use Ripley's K function and L function 

## Compile and package

### Prerequisites
Please make sure you have the following software installed on your local machine:

* For Scala: Scala 2.11, SBT
* For Java: JDK 1.8, Apache Maven 3

### Git Clone
```
$ git clone https://github.com/jiayuasu/GeoSparkTemplateProject.git
```

### GeoSpark Scala Template Project

```
$ cd ./geospark/scala
$ sbt assembly
```

### GeoSpark Java Template Project

```
$ cd ./geospark/java
$ mvn clean install
```

### GeoSpark-SQL Scala Template Project

```
$ cd ./geospark-sql/scala
$ sbt assembly
```

### GeoSpark-Viz Scala Template Project

```
$ cd ./geospark-viz/scala
$ sbt assembly
```
### GeoSpark-Viz Java Template Project

```
$ cd ./geospark-viz/java
$ mvn clean install
```
### GeoSpark Analysis Project

```
$ cd ./geospark-analysis
$ sbt assembly
```

### Submit your fat jar to Spark
After running the command mentioned above, you are able to see a fat jar in `./target` folder. Please take it and use `./bin/spark-submit` to submit this jar.

To run the jar in this way, you need to:

* Either change Spark Master Address in template projects or simply delete it. Currently, they are hard coded to `local[4]` which means run locally with 4 cores.

* Change the dependency packaging scope of Apache Spark from "compile" to "provided". This is a common packaging strategy in Maven and SBT which means do not package Spark into your fat jar. Otherwise, this may lead to a huge jar and version conflicts!

* Make sure the dependency versions in build.sbt and POM.xml are consistent with your Spark version.

## Run template projects locally
We highly suggest you use IDEs to run template projects on your local machine. For Scala, we recommend IntelliJ IDEA with Scala plug-in. For Java, we recommend IntelliJ IDEA and Eclipse. With the help of IDEs, **you don't have to prepare anything** (even don't need to download and set up Spark!). As long as you have Scala and Java, everything works properly!

### Scala
Import the Scala template project as SBT project. Then run the Main file in this project.

### Java
Import the Java template project as Maven project. Then run the Main file in this project.

### Note
* After running your GeoSpark-Viz template project, **you should be able to see a folder at `./target/demo`**. This folder contains all the raster/vector images generated by GeoSparkViz using test data.

* For IntelliJ IDEA users, you probably have to click "File->Project Structure->Global Libraries-> + >From Maven..." to add Spark-core, GeoSpark and Babylon Maven Dependencies in order to run projects in the IDE.
