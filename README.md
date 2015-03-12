# Recipe for Converting to MPL 2.0 HD

1. Edit pom.xml to add the license-maven-plugin
        ```xml
        <plugin>
        	<groupId>com.mycila</groupId>
        	<artifactId>license-maven-plugin</artifactId>
        	<version>2.6</version>
        	<configuration>
        		<header>license-header.txt</header>
        		<includes>
        			<include>**/*.java</include>
        			<include>**/*.txt</include>
        			<include>**/*.xml</include>
        		</includes>
        		<excludes>
        			<exclude>**/license-header.txt</exclude>
        			<exclude>.git/**</exclude>
        			<!-- From gitignore -->
        			<exclude>.idea/**</exclude>
        			<exclude>target/**</exclude>
        			<exclude>bin/**</exclude>
        			<exclude>tmp/**</exclude>
        			<exclude>.settings/**</exclude>
        			<exclude>.externalToolBuilders/</exclude>
        			<exclude>nbproject/private/</exclude>
        			<exclude>build/</exclude>
        			<exclude>bin/</exclude>
        			<exclude>nbbuild/</exclude>
        			<exclude>dist/</exclude>
        			<exclude>nbdist/</exclude>
        			<exclude>nbactions.xml</exclude>
        			<exclude>nb-configuration.xml</exclude>
        			<exclude>**/dwr-modules.xml</exclude>
                    <exclude>build-number.txt</exclude>
        		</excludes>
        	</configuration>
        	<executions>
        		<execution>
        			<goals>
        				<goal>check</goal>
        			</goals>
        		</execution>
        	</executions>
        </plugin>
        ```
2. Add LICENSE (remove old license.txt)
3. Add license-header.txt
4. Add gitattributes as `.gitattributes`
5. Convert line endings
        # may need to be repeated to process last entry
        $ scan-newlines | xargs dos2unix
6. Scan for any other licenses
        $ scan-licenses
7. Format licenses
        $ mvn license:format
8. Check for any old licenses
        $ grep -R -e "OpenMRS Public" *
