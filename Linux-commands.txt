Linux Commands
Day3 Terminal Cmds - Practice Problems

1. Get user infor from /etc/passwd and change ownership of user's home directory 
cat /etc/passwd 
1a) ls -l /etc/passwd
1b) awk < /etc/passwd -F: '{ print $1 }'
1c) awk -F ':' '$3>=1000 {print "User ID:"$1","$3}'
1d) awk -F":" '{print $6}' /etc/passwd | sort
1e) echo $HOME or ls -l /home

2. Move files from one folder to the respective folders 
2a) cat > abc.txt 
    cat > def.txt 
    cat > ghi.txt
    cat > jkl.txt
2b) echo *.txt

2c) fullfilename="/E/BL419/Day3/abc.txt"
filename=$(basename "$fullfilename")
fname="${filename%.*}"
ext="${filename##*.}"
echo $fname
echo $ext

2d) mkdir abc
    mkdir def
    mkdir ghi
    mkdir jkl

2e) mv abc.txt abc
    mv def.txt def
    mv ghi.txt ghi
    mv jkl.txt jkl

3. Append current date to all log files name which has extension .log.1 from a folder
3a) mkdir abc.log.1
    mkdir def.log.1
    mkdir ghi.log.1
    mkdir jkl.log.1
    mkdir mno.log.1
3b) echo *.log.1

3c) fullfilename="/E/BL419/Day3/abc.log.1"
filename=$(basename "$fullfilename")
fname="${filename%.*}"
ext="${filename##*.}"
echo $fname
echo $ext

3d) date | awk '{print $3 " " $2 " " $6 " " }'
3e) echo abc-"`date +"%d%m%Y"`".log

4. Archive the files from /var/log folder which have modifified 7 days ago & move it to your backup folder
4a) find $DIR -mtime -7 -type f
4b) mv * backupfolder

5. Check if a folder exists or not. If it's not present, create it
5a) test -d "Day3" && echo "Found/Exists" || echo "Does not exist"
5b) dir = "foo"
if [ -d $dir ]
then
    echo "Directory already exists"
else
    mkdir $dir
fi

6. Execute command "hello" & "ls" & check it's execution status & print whether command executed successful or not
6a) hello
6b) Execution status of hello command = bash: hello: command not found - 
6c) ls
6d) Execution status of hello command = Executed successfully & it shows list of files & directories

7. Create process list table displays process id, parent process id, command name, % of memory consumption, %cpu utilization
watch -n 1 'ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head'

8.Data Analysis / Manipulation AWK
i) cat data.csv | awk '$4>100000 {print $2 " " $7}'
a) cat data.csv | awk '$4>100000'
b) cat data.csv | awk '{print $2 " " $7}'

ii) grep -i captain data.csv | awk '{sum+=$7} END {print sum/NR}'
a) grep -i captain data.csv
b) cat data.csv | awk '{sum+=$7} END {print sum}'

iii a & b) cat data.csv | awk '$5>=7000 && $5<=10000 {print $3 " " $5}'


iv a & b) cat data.csv | awk '{sum+=$4} END {print sum/NR}'
