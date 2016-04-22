1. Main runner class should look like this 

```
public class RunnerCukes {

    @Test
    public  void testCukesRunner() throws Exception {
        ParallelThread parallelThread = new ParallelThread();
        parallelThread.runner("");
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    }
}

```

2.Extend your Steps to ExtentCucumberFormatter(It is a part of dependencies which takes care of starting appium server before every feature and destroys the appium server after the feature)

```
public class SampleSteps extends ExtentCucumberFormatter {

    @Given("^I have the this useless scenario$")
    public void uselessScenario() {
    }

    @When("^I click on (\\d+) number")
    public void I_sleep_for_seconds(int arg1) throws InterruptedException {
        getDriver().findElementByXPath(".//*[@text="+arg1+"]").click();
    }

    @Then("^It should finnish$")
    public void It_should_finnish() {
    }
}

```

3. Make sure your pom.xml is as below 

```
<repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
    </repositories>

    <pluginRepositories>
        <pluginRepository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </pluginRepository>
    </pluginRepositories>

    <dependencies>
        <dependency>
           <groupId>com.github.saikrishna321</groupId>
           <artifactId>AppiumTestDistribution</artifactId>
           <version>4.0.2</version>
        </dependency>
        <dependency>
            <groupId>com.github.saikrishna321</groupId>
            <artifactId>cucumber-jvm-parallel-plugin</artifactId>
            <version>2.0.9</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.18.1</version>
            </plugin>
            <plugin>
                <groupId>com.github.saikrishna321</groupId>
                <artifactId>cucumber-jvm-parallel-plugin</artifactId>
                <version>2.0.9</version>
                <executions>
                    <execution>
                        <id>generateRunners</id>
                        <phase>validate</phase>
                        <goals>
                            <goal>generateRunners</goal>
                        </goals>
                          <configuration>
                            <!-- Mandatory -->
                            <!-- comma separated list of package names to scan for glue code -->
                            <glue>foo, bar</glue>
                            <!-- These are the default values -->
                            <!-- Where to output the generated tests -->
                            <outputDirectory>src/test/java/output</outputDirectory>
                            <!-- The directory containing your feature files.  -->
                            <featuresDirectory>src/test/resources/features/</featuresDirectory>
                            <!-- Directory where the cucumber report files shall be written  -->
                            <cucumberOutputDir>target/cucumber-parallel</cucumberOutputDir>
                            <!-- comma separated list of output formats -->
                            <format>json</format>
                            <!-- CucumberOptions.strict property -->
                            <strict>true</strict>
                            <!-- CucumberOptions.monochrome property -->
                            <monochrome>true</monochrome>
                            <!-- The tags to run, maps to CucumberOptions.tags property -->
                            <tags>"@complete", "@accepted"</tags>
                            <!-- If set to true, only feature files containing the required tags shall be generated. -->
                            <!-- Excluded tags (~@notMe) are ignored. -->
                            <filterFeaturesByTags>false</filterFeaturesByTags>
                            <!-- Generate TestNG runners instead of JUnit ones. -->
                            <useTestNG>false</useTestNG>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>

```


###Run Test from CommandLine

```
mvn clean -Dtest=RunnerCukes test
```