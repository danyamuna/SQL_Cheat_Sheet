> 1- The keyword " Percent " cannot be used  as a table name.
> 
> 2- One of the common mistakes : Place a comma at the end of each line; the comma should only be placed when the block is finished.
> 
> 3-The **join Left** show all data even is Null
>
> 4- In order to generate random values.
> use **NEWID()**
>
> Order By NEWID();

SQL
```md
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE = OFF;
(ملاحظة: إيقافها قد يقلل الأداء بشكل طفيف جداً غير ملحوظ إلا في الأنظمة الضخمة التي تضيف آلاف الصفوف في الثانية، ولكنه يضمن لك عدم حدوث قفزات مجدداً).
```
> 5- select SCOPE_IDENTITY();
