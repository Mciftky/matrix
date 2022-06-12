#include <stdio.h>
#include <stdlib.h>
void matrisYazdir(int **, int, int);
void transpozYazdir(int**, int, int);                //fonksiyon protipleri

int main (int argc, const char *argv[])
{
int ** matris;
int satirSayisi, sutunSayisi;

printf("Olusturacagınız matrisin satir sayisini giriniz:");
scanf("%d", &satirSayisi);

printf("Olusturacaginiz matrisin sutun sayisini giriniz:");
scanf("%d",&sutunSayisi);

matris=(int**)malloc(sizeof(int*)*satirSayisi);      // satir baslarini tutacak dizi icin yer ayırdık.

int i,j;
for(i=0; i< satirSayisi; i++)                        // her bir satır için sütun sayısı kadar yer ayıralım.
    matris[i]=(int*)malloc(sizeof(int)*sutunSayisi);

    printf("-----------------\n");
    printf("Matris icin elemanları giriniz:\n");     //matrisin elemanlarını satır satır okuyalım.
    printf("-----------------\n");

for(i=0; i< satirSayisi; i++){
    for(j=0; j< sutunSayisi; j++){
        printf("Matris[%d][%d]= ", i, j);
        scanf("%d",&(matris[i][j]));
    }
}

    printf("-----------------\n");
    printf("Girdiginiz matris:\n");     //matrisYazdir fonksiyonunu kullanarak matrisimizin degerlerini konsola yazdıralım.
    printf("-----------------\n");
    matrisYazdir(matris,satirSayisi,sutunSayisi);


    printf("-----------------\n");
    printf("Matrisin transpozu:\n");     //matrisin transpozunu bulan ve yazdıran fonk. cagıralım ve matrisin transpozunu ekrana yazdıralım.
    printf("-----------------\n");
   transpozYazdir(matris,satirSayisi,sutunSayisi);

   for(i=0;i<satirSayisi; i++)
    free(matris[i]);                   //matrisin tum elemanlarını bosaltalım mallocla ayırdıgımız her seyi temizleyelim.

   free(matris);                       //matrisin satir baslarini tutan isaretcilerin tuttugu bellek alanlarını bosaltalım.

return 0;
}
void matrisYazdir(int** matris,int satir,int sutun)
{
int i,j;
for (i=0; i<satir;i++){
    for(j=0;j<sutun; j++){   //bu fonk. satır ve sutun sayisi parametre olarak verilen bir matrisin tüm elemanlarını gezerek konsola yazdırır.Matrisler 2 boyutlu oldugu icin tek bir döngü yerine iç içe for döngüleri kullanılmıstır.
        printf("%5d",matris[i][j]);
    }
    //icteki for her bir satir için sutunları yazdirir.İctkeki for döngüsünden cıkıldıgında ilgili satır yazdırılmış demektir,dolayısıyla asagıdaki komutla bir alt satıra gecilir.
    printf("\n");
    }
}
void transpozYazdir(int**matris,int satir, int sutun){
int i,j;
for(i=0; i< sutun; i++){
    for(j=0; j<satir; j++){
printf("%5d", matris[j][i]);

}
printf("\n");
}
}

