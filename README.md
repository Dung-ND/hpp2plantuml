# DungND
## Generate UML diagram from Cpp project (OOP design) on Ubuntu

The package does two tasks:

- Read header files in the project, and generate classes and their relationship in plantuml format
- Generate UML Class diagram in image format

## How to use

- Extract the package:  
```unzip -q cpp_uml_dungnd.zip```
- Go inside the package and install it:  
    ```cd hpp2plantuml```  
    and  
    ```pip install .```

- There is a folder called "Example", it contains some code implement some behavioral design pattern
- Go inside the "example" folder:  
```cd example```  
- There is an example how to run the package, to export UML diagram from a folder. Run it:  
```./export_observer_example.sh```  
It will generate two files: Observer.puml and Observer.svg  
.puml is the description file in "puml" format  
.svg is the image file of generated uml class diagram  
- You can test with another folder using command:  
```hpp2plantuml -f path_to_folder```  
For example:  
```hpp2plantuml -f Behavioral/Command```

## Some configuration:
- Output filename can be specified by "-o" flag
- If you only want to generate ".puml" file, and export to diagram image using java later, use:  
```hpp2plantuml -f Behavioral/Command -s no```  
 to prevent sending request to server
- "-d" flag will extract dependency relationships from method arguments
- The diagram rendering is done by sending a request to a public server (http://www.plantuml.com/plantuml)
 It is for testing. If you want to protect your privacy, let's run a local server for rendering. And also, for folder with lots of class, running in local server is more stable than public online server  
     ```docker pull plantuml/plantuml-server```  
    and then:  
     ```docker run --detach --publish 8080:8080 plantuml/plantuml-server```

    Requirement: [docker](https://docs.docker.com/desktop/install/ubuntu/) installed
    After that, the package can be run against local server as:
    `hpp2plantuml -f Behavioral/Command -s http://127.0.0.1:8080`  
    Option "-s" specify the server to render the image diagram.
    ##### Another option is to use java tool to render image from ".puml" file, no need for docker server. Check "Additional information" part below


## Additional information

If your computer has java installed, you can render puml file into image diagram with simple command as guided here: https://plantuml.com/command-line  
`java -jar plantuml.jar filename.puml -svg`

## Resources used in this package

- [hpp2plantuml](https://github.com/thibaultmarin/hpp2plantuml) - Package for generating ".puml" from cpp header
- [PlantWeb](https://github.com/carlos-jenkins/plantweb) - Package for sending request to server for rendering diagram
- [plantuml](https://github.com/plantuml/plantuml/releases) - plantuml.jar file for generating diagram using java

## Please give me some feedback if you have any. Thank you!
[DungND](dungnd.vx@gmail.com)