#!/bin/bash
# Skrypt segregujacy (lub usuwajacy) pliki wg podanego rozszerzenia (lub nazwy)
# (c) Grabowski Marek 06.01.2012
clear
echo -e "_________________Segregator 0.0.3 Main Menu___________________"

SELECTION=("Sortuj pliki wg rozszerzenia" "Sortuj pliki wg nazwy" "Usun pliki wg rozszerzenia" "Usun pliki wg nazwy"  "Wyjscie")
select options in "${SELECTION[@]}"; do

if [ "$options" = "Sortuj pliki wg rozszerzenia" ]; then
echo -e "\nPodaj rozszerzenie plikow, ktore chcesz posortowac"

read extension

echo -e "\nPodaj sciezke do miejsca z plikami .$extension"
read dir
 
sorted_dir="$dir/$extension"
quantity=`ls "$dir" | grep "$extension"`

mkdir -p "$sorted_dir"

for image in "$dir"/*.$extension; do 
mv -f "$image" "$sorted_dir"
echo -e "\nZrobione!"
done

elif [ "$options" = "Sortuj pliki wg nazwy" ]; then
echo -e "\nPodaj nazwy plikow, ktore chcesz posortowac"
read name

echo -e "\nPodaj sciezke do miejsca z plikami $name .*"
read dir

sorted_dir="$dir/$name"
quantity=`ls "$dir" | grep "$name"`

mkdir -p "$sorted_dir"

for image in "$dir"/$name.*; do
mv -f "$image" "$sorted_dir"
echo -e "\nZrobione!"
done

elif [ "$options" = "Usun pliki wg rozszerzenia" ]; then
echo -e "\nPodaj rozszerzenie plikow, ktore chcesz usunac"

read extension

echo -e "\nPodaj sciezke do miejsca z plikami .$extension"
read dir

quantity=`ls "$dir" | grep "$extension"`
for image in "$dir"/*.$extension; do
rm  "$image" 
echo -e "\nZrobione!"
done


elif [ "$options" = "Usun pliki wg nazwy" ]; then
echo -e "\nPodaj nazwy plikow, ktore chcesz usunac"
read name

echo -e "\nPodaj sciezke do miejsca z plikami $name .*"
read dir

quantity=`ls "$dir" | grep "$name"`
for image in "$dir"/$name.*; do
rm  "$image"
echo -e "\nZrobione!"
 done

elif [ "$options" = "Wyjscie" ]; then
        echo "Do widzenia."
    exit

else
    clear;
    echo "Wybierz ktoras z opcji"
echo " (nacisniecie enter ponownie wyswietla liste)"
fi
done
