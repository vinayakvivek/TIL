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
- Then move HEIC files to another folder,
    ```
    mkdir convert
    mv *.HEIC convert/
    ```
- Use `ImageMagick` tool to group convert HEIC images to jpg.
    ```
    cd convert
    magick mogrify -monitor -format jpg *.HEIC
    ```
- Delete HEIC files and move jpgs.
    ```
    rm *.HEIC
    mv *.jpg ../
    cd ../
    rm -r convert
    ```
