# nexusTest

Project is composed by a library project and an app. The library project creates a .aar file. 
A nexus instance runs at localhost:8081

File is deplyoed on a local instance of Nexus through this script:

mvn deploy:deploy-file -DgroupId=com.mycompany -DartifactId=mytestlibrary -Dversion=0.5.355 -DgeneratePom=true -Dpackaging=aar -DrepositoryId=hosted-test1 -Durl=http://127.0.0.1:8081/nexus/content/repositories/hosted-test1 -Dfile=mylibrary-debug.aar

you need to add the credentials to the .m2/settings.xml file see:

    <server>
      <id>hosted-test1</id>
      <username>admin</username>
      <password>admin123</password>
    </server>

The app downloads the library from there (latest version) compiles with it.

By tyoing "gradle update", the release apk is uploaded to nexus.

