#LAB REPORT 3 - EXPLORING COMMANDS

##grep supremacy##
For this Lab Report I am going to be exploring interesting flags of grep command. I chose grep solely due to how interesting I thought it was while using it for the tasks in the skill demo. 
While looking for quick ways to do tasks like searching for a name through all the files, etc I discovered that grep can be used in combination with multiple flags for efficieny. 

**grep -l**

My first example is using `grep -l "string" <file directory>` to search for a particular string in a given directory
I used the command `grep -l "Lucayans" written_2/*/*/*.txt` to search for the word `Lucayans` through out all of the `.txt` files in the folder `written_2` 
The output for the command is as follows:
![grep -l](https://github.com/madhoolikacvss/lab_rep_3/blob/main/grep%20l%20simple.jpg)

Here, -l is a flag that is used to display all of the file names (only) that contain the string given in the command. As only Bahamas-History.txt contained that string, it was the output.
I  gave the command another word to see how the output looks like and to explore its drawbacks - the command was `grep -l "Bahamas" written_2/*/*/*.txt`, and the output was as follows:
![Bahamas](https://github.com/madhoolikacvss/lab_rep_3/blob/main/grep%20l%20bahamas.jpg)
As we can see here, the output has gotten longer, as there are multiple files with the word "Bahamas". When wanting to look for files with a particular string within a particular folder, this command comes in really handy as the output clearly shows all of the files names - exactly what we want!
But there a few drawbacks to this command. Firstly, we are lucky that "Bahamas" occurs in only a handful of files. This might not be the case for larger data bases or more common words. In such cases, we will endup with hunders of files being spit out my the terminal as all of them have the given string. 
Second issue is that we are giving the pattern of the files we want grep to search for - `written_2/*/*/*.txt` - however, for bigger folders, we cannot be typing in tens of * and /. Instead, we need a command that searches the entire folder recursively.

**grep -rl**
Tackling the second problem first - searching the files recursively
The flag `-rl` is a combination of two flags, one of which we have seen earlier, `-l`. The second flag we are using here is `-r` which searched for the pattern string in all of the files in the given directory and its sub directories.
When using `-rl` you do not need to enter the target directory or any pattern such as `written_2/*/*/*.txt`, as shown below. 
![-rl](https://github.com/madhoolikacvss/lab_rep_3/blob/main/grep%20rl.jpg)
)
For example if you did not want to search the entire folder and just a file inside the given folder as shown below where I did not want to look through all of written_2 but instead travel_guides that's present in written_2:
![travel](https://github.com/madhoolikacvss/lab_rep_3/blob/main/cd%20into%20travel.jpg)

Or, you could type in the filder name as given below (my current directory was skill-demo1-data and I added the folder name written_2 as I wanted to search only in that folder):
![typing in folder name](https://github.com/madhoolikacvss/lab_rep_3/blob/main/not%20travel.jpg)

Using `-rl` is much simple as you do not have to remember/type in the file pattern as you do using `-l`

**grep -rl "string" | wc -l**
Now that we discovered how useful `-rl` is, we can use it in combination with another command to solve the first issue with `grep - l` - an overly long ouput.
We can use the command `wc - l` that counts the number of file names that have been returned by `grep -rl "string"` and outputs the number.
Although `wc` is not a flag for `grep` this example shows how useful and effective combinign two commands can be. 
In the example below, my input was `grep -rl "Lucayans" | wc -l` which gave out the following output:
1[ rl and wc](https://github.com/madhoolikacvss/lab_rep_3/blob/main/rl%20and%20wc%20example%201.jpg)

Although this might not seem like a lot, the true potential of this command can be seen in the example below, where the number of files have the given word are in hundreds.
![rl wc ex 2](https://github.com/madhoolikacvss/lab_rep_3/blob/main/rl%20and%20wc%20example%202.jpg)

**grep -L "string" | wc -l**
In another world, you'd want to know the number of files that do not have a particular word. 
Just like how `-l` search for a string in files and gives those file names as the output, `-L` outputs the files that do not have the given string (big brothers do be opposing the younger one all the time). 
In the example given below, I am using `-r` in combination with `-L` to find out how many files do not have the word "Lucayans"
![big L](https://github.com/madhoolikacvss/lab_rep_3/blob/main/grep%20L.jpg)

As expected, there are too many file names, and to solve that, we can again combine this comman with `|wc -l` - gives us the number fo files that do not have "Lucayans"
![not L and wc](https://github.com/madhoolikacvss/lab_rep_3/blob/main/not%20rl%20and%20wc.jpg)


I have used [this](https://www.vogella.com/tutorials/UnixGrep/article.html) website to help me with understanding the uses and purposes of each flag that grep has. 