#Zaliczenie
```sh
#!/bin/bash
# Skrypt segregujacy (lub usuwajacy) pliki wg podanego rozszerzenia (lub nazwy)
# (c) Grabowski Marek 06.01.2012
clear
echo -e "_________________Program  0.0.3____________________"

echo -e "-----------------"
echo -e "      MENU       "
echo -e "-----------------"
echo -e "\n1: Sortuj pliki wg rozszerzenia"
echo -e "\n2: Sortuj pliki wg nazwy"
echo -e "\n3: Usun pliki wg rozszerzenia"
echo -e "\n4: Usun pliki wg nazwy"
echo -e "\n5: Wyjscie" 

echo -e "\nWybor:"
read i

case $i in
"1")
echo -e "\nPodaj rozszerzenie plikow, ktore chcesz posortowac"
read extension

echo -e "\nPodaj pelna sciezke do miejsca z plikami .$extension"
read dir
 
sorted_dir="$dir/$extension"
quantity=`ls "$dir" | grep "$extension"`

mkdir -p "$sorted_dir"

for image in "$dir"/*.$extension; do 

mv -f "$image" "$sorted_dir"

done
;;



"2")
echo -e "\nPodaj nazwy plikow, ktore chcesz posortowac"
read name

echo -e "\nPodaj pelna sciezke do miejsca z plikami $name .*"
read dir

sorted_dir="$dir/$name"
quantity=`ls "$dir" | grep "$name"`

mkdir -p "$sorted_dir"

for image in "$dir"/$name.*; do

mv -f "$image" "$sorted_dir"

done
;;

"3")
echo -e "\nPodaj rozszerzenie plikow, ktore chcesz usunac"
read extension

echo -e "\nPodaj pelna sciezke do miejsca z plikami .$extension"
read dir

quantity=`ls "$dir" | grep "$extension"`
for image in "$dir"/*.$extension; do
rm -f "$image" 

done
;;

"4")
echo -e "\nPodaj nazwy plikow, ktore chcesz usunac"
read name

echo -e "\nPodaj pelna sciezke do miejsca z plikami $name .*"
read dir

quantity=`ls "$dir" | grep "$name"`
for image in "$dir"/$name.*; do
rm -f "$image" 

done
;;


5)
;;


*) echo "Wpisales niepoprawny numer." ;;
esac

echo -e "\n______________________Koniec!______________________"
```

