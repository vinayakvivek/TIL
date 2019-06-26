# Renaming and converting HEIC images 
> 26/06/2019

- To rename image files with numbers in the chronological order,
```bash
index=1;
for f in $(ls -vtr);
do
    ext="${f##*.}"
    mv $f ${index}.$ext
    index=$(($index + 1))
done
```
