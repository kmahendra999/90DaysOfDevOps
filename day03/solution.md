
# Basic Linux Commands

1. To view what's written in a file.
    - ``` cat filename ``` 
    
![3 1](https://user-images.githubusercontent.com/76457594/210305889-d19f82d5-dbb1-46fc-99e2-b217146b6e8a.png)



2. To change the access permissions of files.
   
    - ``` chmod 777 foldername ``` 

![Uploading 3.2.png…]()

3. To check which commands you have run till now.

   - ``` history ``` 

  ![Uploading 3.3.png…]()

4. To remove a directory/ Folder.

      - ``` rm filename ``` 
      
 ![3 4](https://user-images.githubusercontent.com/76457594/210308917-7281e0eb-6fcb-4554-8ffe-835cf0b961d1.png)

    -  ``` rmdir foldername ``` 
    
 ![3 4b](https://user-images.githubusercontent.com/76457594/210309299-367e6253-7e11-4ead-a19c-6eb3922780d1.png)

5. To create a fruits.txt file and to view the content.
    - ``` vim fruits.txt ``` 
    -  ```  cat fruits.txt ``` 
   
![3 5](https://user-images.githubusercontent.com/76457594/210311435-e6f8aa0c-dc0c-44a6-84e7-6e4c91e4ea87.png)


 
Task: What is the linux command to

To view what's written in a file.
```cat filename```

To change the access permissions of files.
```chmod 777 foldername```

To check which commands you have run till now.
```history```

To remove a directory/ Folder.
```rm filename```

To create a fruits.txt file and to view the content.
```echo "testststsetst" >> fruits.txt```
```cat fruits.txt```

Add content in devops.txt (One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.
```echo -e "Apple\nMango\nBanana\nCherry\nKiwi\nOrange\nGuava" > devops.txt```

To Show only top three fruits from the file.
```head -n 3 fruits.txt```

To Show only bottom three fruits from the file.
```tail -n 3 fruits.txt```

To create another file Colors.txt and to view the content.
```vim Colors.txt```
```write contetns```
```:wq!```
```cat Colors.txt```

Add content in Colors.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey.
```vim Colors.txt```
Red
Pink
White
Black
Blue
Orange
Purple
Grey
:wq!

To find the difference between fruits.txt and Colors.txt file.
```diff fruits.txt Colors.txt```
