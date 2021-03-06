# kotlinx.coroutines release checklist

To release new `<version>` of `kotlinx-coroutines`:

1. Checkout `master` branch: <br> 
   `git checkout master`

2. Retrieve the most recent `master`: <br> 
   `git pull`

3. Merge `develop` branch unto `master`: <br>
   `git merge origin/develop` 

4. Search & replace `<old-version>` with `<version>` across the project files. Should replace in:
   * [`README.md`](README.md)
   * [`coroutines-guide.md`](coroutines-guide.md)
   * [`gradle.properties`](gradle.properties)
   * [`ui/kotlinx-coroutines-android/example-app/gradle.properties`](ui/kotlinx-coroutines-android/example-app/gradle.properties)    
   * [`ui/kotlinx-coroutines-android/animation-app/gradle.properties`](ui/kotlinx-coroutines-android/animation-app/gradle.properties)    
   * Make sure to **exclude** `CHANGES.md` from replacements.
  
5. Write release notes in [`CHANGES.md`](CHANGES.md):
   * Use old releases as example of style.
   * Write each change on a single line (don't wrap with CR).
   * Study commit message from previous release.

6. Commit updated files for new version: <br>
   `git commit -a -m "Version <version>"`
   
7. Push new version into `master`: <br>
   `git push`   

8. On [TeamCity integration server](https://teamcity.jetbrains.com/project.html?projectId=KotlinTools_KotlinxCoroutines):
   * Wait until "Build" configuration for committed `master` branch passes tests.
   * Run "Deploy" configuration with the corresponding new version.    

9. In [GitHub](http://github.com/kotlin/kotlinx.coroutines) interface:
   * Create new release named as `<version>`. 
   * Cut & paste lines from [`CHANGES.md`](CHANGES.md) into description.    

0. Build and publish documentation for web-site: <br>
   `site/deploy.sh <version> push`
   
1. In [Bintray](https://bintray.com/kotlin/kotlinx/kotlinx.coroutines) admin interface:
   * Publish artifacts of the new version.
   * Wait until newly published version becomes the most recent.
   * Sync to Maven Central.
   
2. Announce new release in [Slack](http://kotlinlang.slack.com)   

3. Switch into `develop` branch: <br>
   `git checkout develop`
   
4. Merge release from `master`: <br>
   `git merge master`
   
5. Push updates to `develop`: <br>
   `git push`      
