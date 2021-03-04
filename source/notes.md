# Notes

## Access Info

You can access your CloudStore dashboard here:-

https://droidscript.cloud/admin/admin.html

user: wisemanworking@gmail.com
pass: gareth.pass

You can see that your API key is
ClhXXPi5bjcTjGjVqqp2

## TODOs

- <strike>Install Slate GitHub project on local machine</strike>
- <strike>Find out how to generate static files and send to David</strike>
- Solution:
  - Open up docker image in terminal window
  - run > bundle exec middleman build
  - This build all static web pages to the build folder
- Add Merge function to cloudstore doc (https://lodash.com/docs#merge)
- Add Delete function to cloudstore doc
- Document media files (upload, delete, manage, password protect)
- Document dashboard (cloudstore control panel)
- write demo code to test

===================
- Sub headings for web page:
  - Data
  - Media
  - Dashboard

  - Examples for password protection 
    - News updates - (data): select editors allowed update the data file with a password prompt
    - News flash or promotion image - Loaded through CloudStore dashboard or special admin app or admin mode/section with password prompt
    - Media paths are unique and unguessable (non sequential) for safe sharing publically or privately
    - E-commerce

 - Add warning to not hard code password into code (use warning alert)

 - Add password argument for media Upload function


 - Background image
 - Add password to Save function - DONE
 - Document how to include the CloudStore class. One example from a HTML page. Move cloud = new CloudStore( "<YOUR_CLOUDSTORE_KEY>" ) into this part
    - remove on other examples - DONE
  - change console.warn to console.error - DONE
  - Merge function:
    The Merge function recursively merges values passed with the source object, replacing any existing data and adding new data. Also supports arrays.
    - remove other bullet points - DONE
  - Change format of 'cloud.List( "steve", callback )' - should appear as code line - DONE
  - Update CloudStore class:
    - Use fetch in SendData method (replace httprequest with sendData)
    - Use camelCase for method names
    - Copy RateCheck code to top of all blocks
    

 -    
 - 

===================

## DONE

- Fri 30-10: 3hrs Slate docs UI changes/layout.formating
- Mon 02-11: 2hrs Building static html version. New documentation added. Dark theme added
- Tue 03-11: 2hrs Continuation of documentation.  Load and Upload methods added to CloudStore doc
- Wed 04-11: 2hrs Discussion of structure, layout, styling and further dev tasks.  Modification of layout and further styling
- Thu 05-11: 2hrs Continuation of documentation and tidying up of code examples to change from Greenhouse to Shopping List
- Mon 09-11: 4hrs Added Media documentation, corrected mistakes and extended Data File documentation.  Added documentation for new dashboard UI
- Tue 10-11: 2hrs Finish up of first version of documentation
- Wed 18-11: 4hrs Discussed status and next steps. Made changes to text and images
- Thu 19-11: 1hr Change all refs for admin control panel to admin dashboard; Updated all pictures of admin dashboard; Updated password protection and tidied up more of the document
- Mon 23-11: 2hrs - Fixes to callback changes.  Updated image and text for overview. Fixed other small changes
- Tue 24-11: 2hrs - Fixes. Changed ShowPopup to console.warn and console.log.  Removed instances of app. Changed cloud = CreateCloudStore to cloud = new CloudStore
- Wed 25-11: 2hrs - General maintenance and review. Update to CloudStore class file
- Thu 26-11: 4hrs - Password to Save function, background image added, Merge function desc updated, overview added, new CloudStore entries removed from examples, console.warn changed to console.error.  Modified cloudstore.js to use fetch instead of xmlhttprequest.   Still needs testing.
- Fri 27-11: 4hrs - Final changes to docs and updates to cloudstore.js.  Tested new changes.  Released version to GitHub ready for production
- Mon 2-12: 2hrs - Made requested changes to cloudstore.js
- Thu 3-12: 2hrs - Discussed slate docs and next ideas.  Started on game ideas to demo cloud store
- Mon 7-12: 4hrs - Started to build Maths game
- Wed 9-12: 3hrs - Continued working on Maths game
- Thu 10-12: 2.5hrs - Continued working on Maths game. Sent v1 to David in email
- Wed 16-12: 2hrs - Tested video recording and went through app code
- Thu 17-12: 2hrs - Modified code to improve layout and sync with other DroidScript examples
