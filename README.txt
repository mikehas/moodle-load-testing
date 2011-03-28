Moodle JMeter Tests:

This test suite is designed to benchmark or stress test a moodle instance. Only run this in a development environment.

CONTENTS:

Python Script:
testprep.py - This file should be run from the terminal.  When executed with the -o option, it will create a set of 6 files in the directory specified by -o. Without the -o option it may overwrite previous test files.

The created files compose a set of jmeter files (usef for creating courses, running tests, and deleting courses) and text files (manual student batch create/delete files and student credentials.)

EXAMPLE FILES:
1_create_courses.jmx                Logs in as administrator user and creates courses
2_create_students_25s_3c_3cpers.txt Used to manually import users
3_run_test.jmx                      Performs primary tests using studentcredentials
4_delete_students_25.txt            Used to manually remove users
5_delete_courses.jmx                Logs in as administrator user and deletes courses
student_credentials_25.txt          Student credentials used in JMeter tests.

TESTING PROCEDURE:

1. Open testprep.py and edit settings according to your environment.
2. Execute './testprep.py -o testXX' This will create a folder called testXX with all the files you need to run the test.
3. Run 1_create_courses.jmx. 'jmeter -t moodle_1_setup.jmx &'
4. Upload users by uploading 2_create_students_25s_3c_3cpers.txt file. Open Moodle -> Users -> Accounts -> Upload Users.
5. Run 3_run_test.jmx.
6. Remove users by uploading 4_delete_students_25.txt file. Use the same moodle page as step 4 above.  To delete users you must select the allow delete dropdown option.
7. Run 5_delete_courses.jmx to remove courses. (Note you must manually specify the DELSTARTVAL in this jmx file before running. This value should be the moodle ID of the first automatically created JCOURSE.  Not doing so, could be bad :)