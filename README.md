# jfx
JFX for the Stealify Java Stack

Scene Builder is only available as part of the OpenJDK source, fortunately you don’t need to clone the whole JDK and you can grab a snapshot of just the application in a handy tar ball.

http://hg.openjdk.java.net/openjfx

from here select the version of java you’re using – just below the version there should a folder “rt” once inside click on browse (a link on the column down the left side).  Now we can actually see a hierarchy of files, once you have navigated to /apps/scenebuilder/ you can grab an archive in your choice compression method of by using the links on the left.

Refreshingly building is simplicity itself! just run ant in the apps/scenebuilder directory and after a little while you end up with a couple of jars.  Unfortunately as we have ripped it apart from the rest of the source tree the build file won’t work to run scene builder.

It’s easy enough to make your own target and paste it into your projects build file

  <property name="sbpath" location="../scenebuilder/apps/scenebuilder"/>

  <target name="edit-gui"
          description="run javafx scene builder">
    <java fork="true" 
          classname="com.oracle.javafx.scenebuilder.app.SceneBuilderApp"
          >
      <arg value="${src}/main-ui.fxml"/>
      <classpath>
        <pathelement location="${sbpath}/SceneBuilderApp/dist/SceneBuilderApp.jar"/>
        <pathelement location="${sbpath}/SceneBuilderKit/dist/SceneBuilderKit.jar"/>
      </classpath>
    </java>      
  </target>
