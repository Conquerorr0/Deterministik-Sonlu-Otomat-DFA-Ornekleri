# Deterministik Sonlu Otomat (DFA) Örnekleri

Bu depo, Deterministik Sonlu Otomat (DFA) örneklerini içermektedir. Her bir örnek, giriş alfabesi, durumlar ve durumlar arasındaki geçişleri gösteren bir tablo kullanılarak tanımlanmıştır.

## Örnek 1: Çift Sayıları Tanıyan Otomat

Alfabe: {0, 1} (İkili sayılar)  
Durumlar: {q0, q1}  
Başlangıç Durumu: q0  
Bitiş Durumu: q0  

| Durumlar | 0   | 1   |
|:---------|:---:|:---:|
| q0       | q0  | q1  |
| q1       | q1  | q0  |

Bu DFA, girişteki her 0 için q0 durumunda kalır ve her 1 için q1 durumuna geçer. Başlangıç durumu q0'dur ve çift sayıyı tanıyan bir otomat olduğu için q0 durumu bitiş durumudur.

#Kod:
'''


import java.util.Scanner;

//Çift Sayıları Tanıyan Otomat {İkilik sayı sistemine göre}

/*
        Alfabe: {0, 1} (İkili sayılar)
        Durumlar: {q0, q1}
        Başlangıç Durumu: q0
        Bitiş Durumu: q0 
 */

public class Question1 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        final String FINAL_STATE = "q0";
        String state = "q0";
        char letter;

        System.out.print("Sayi: ");
        String word = scanner.next();

        for (int i = 0; i < word.length(); i++) {
            letter = word.charAt(i);

            if (letter != '0' && letter != '1') {
                System.out.println("Yanlis karakter!");
                System.exit(0);
            }

            if (state.equals("q0")) {
                if (letter == '0') {
                    state = "q0";
                } else {
                    state = "q1";
                }
            } else {
                if (letter == '0') {
                    state = "q0";
                } else {
                    state = "q1";
                }
            }
        }

        if (state.equals(FINAL_STATE)) {
            System.out.println(word + " cift sayidir.");
        } else {
            System.out.println(word + " tek sayidir.");
        }
    }
}

'''

## Örnek 2: "AB" Dizisini Tanıyan Otomat

Alfabe: {A, B}  
Durumlar: {q0, q1, q2}  
Başlangıç Durumu: q0  
Bitiş Durumu: q2  

| Durumlar | A   | B   |
|:---------|:---:|:---:|
| q0       | q1  | q0  |
| q1       | q2  | q0  |
| q2       | q2  | q2  |

Bu DFA, girişteki her A'da bir durum ilerler ve "AB" dizisini bulduğunda q2 durumuna geçer. Başlangıç durumu q0'dur ve q2 durumu bitiş durumudur, çünkü "AB" dizisini tanıyan bir otomat olarak tanımlanmıştır.

## Örnek 3: Belirli Bir Diziyi Tanıyan Otomat

Alfabe: {0, 1}  
Durumlar: {q0, q1, q2, q3}  
Başlangıç Durumu: q0  
Bitiş Durumu: q3  

Örnek Dizi: 1010  

| Durumlar | 0   | 1   |
|:---------|:---:|:---:|
| q0       | q1  | q0  |
| q1       | q2  | q0  |
| q2       | q1  | q3  |
| q3       | q3  | q3  |

Bu DFA, girişte belirtilen örnek dizi olan 1010'u tanır. Başlangıç durumu q0'dur ve q3 durumu bitiş durumudur, çünkü örnek dizi tamamlandığında bu duruma geçer.

Bu örnekler, farklı durumlar arasındaki geçişleri ve bir otomatın belirli bir dildeki dizileri nasıl tanıyabileceğini göstermektedir. Gösterilen tablolar, belirli bir dilin tanınması için kullanılabilecek temel bir DFA'nın yapılarını sunmaktadır.
