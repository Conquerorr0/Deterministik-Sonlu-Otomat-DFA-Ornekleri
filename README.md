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

### Kod:

    
    import java.util.Scanner;
    
    public class Question1 {
    
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
    
            final STATES FINAL_STATE = STATES.Q0;
            STATES state = STATES.Q1;
            char letter;
    
            System.out.print("Sayi: ");
            String word = scanner.next();
    
            for (int i = 0; i < word.length(); i++) {
                letter = word.charAt(i);
    
                if (letter != '0' && letter != '1') {
                    System.out.println("Yanlis karakter!");
                    System.exit(0);
                }
    
                if (state == STATES.Q0) {
                    if (letter == '0') {
                        state = STATES.Q0;
                    } else {
                        state = STATES.Q1;
                    }
                } else {
                    if (letter == '0') {
                        state = STATES.Q0;
                    } else {
                        state = STATES.Q1;
                    }
                }
            }
    
            if (state == FINAL_STATE) {
                System.out.println(word + " cift sayidir.");
            } else {
                System.out.println(word + " tek sayidir.");
            }
        }
    }
    
    enum STATES{
        Q0,
        Q1
    }


## Örnek 2: İçinde "AB" Bulunan Kelimeleri Tanıyan Otomat

Alfabe: {A, B}  
Durumlar: {q0, q1, q2, q3}  
Başlangıç Durumu: q0  
Bitiş Durumu: q2  

| Durumlar | A   | B   |
|----------|-----|-----|
| q0       | q1  | q0  |
| q1       | q1  | q2  |
| q2       | q3  | q0  |
| q3       | q3  | q2  |

Bu DFA, içinde "AB" dizisini bulunduran kelimeleri tanır. Girişteki her A harfinde bir durum ilerler ve ardından B harfi geldiğinde q2 durumuna geçer. Başlangıç durumu q0'dur ve q2 durumu bitiş durumudur, çünkü "AB" dizisini içeren kelimeleri tanıyan bir otomat olarak tanımlanmıştır.

## Kod:

    import java.util.Scanner;
    
    
    public class Question2 {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
    
            final STATES FINAL_STATE = STATES.Q2;
            STATES state = STATES.Q0;
            char letter;
    
            System.out.print("Kelime: ");
            String word = scanner.next().toUpperCase();
            
            for (int i = 0; i < word.length(); i++) {
                letter = word.charAt(i);
                
                if(letter != 'A' && letter != 'B'){
                    System.out.println("Hatali karakter!");
                    System.exit(0);
                }
                
                if(state == STATES.Q0){
                    if(letter == 'A'){
                        state = STATES.Q1;
                    }
                    else{
                        state = STATES.Q0;
                    }
                }
                else if(state == STATES.Q1){
                    if(letter == 'A'){
                        state = STATES.Q1;
                    }
                    else{
                        state = STATES.Q2;
                    }
                }
                else if(state == STATES.Q2){
                    if(letter == 'A'){
                        state = STATES.Q3;
                    }
                    else{
                        state = STATES.Q0;
                    }
                }
                else{
                    if(letter == 'A'){
                        state = STATES.Q3;
                    }
                    else{
                        state = STATES.Q2;
                    }
                }
            }
            
            if(state == STATES.Q2)  System.out.println(word + " ototmata tarafindan taninir.");
            else    System.out.println(word + " ototmata tarafindan taninmaz.");
            
        }
    }
    
    enum STATES{
        Q0,
        Q1,
        Q2,
        Q3
    }


## KOD3: '1010' Dizisini Tanıyan Otomat

Durumlar:
- q0: Başlangıç durumu
- q1: İlk '1' karakterini görmüş durum
- q2: '10' dizisini görmüş durum
- q3: Bitiş durumu ('1010' dizisini tamamlamış durum)

Geçişler:
| Durumlar | 0   | 1   |
|----------|-----|-----|
| q0       | q0  | q1  |
| q1       | q0  | q2  |
| q2       | q3  | q1  |
| q3       | q3  | q3  |

Bu DFA, girişte belirtilen örnek dizi olan '1010' dizisini tanır. Başlangıç durumu q0'dur ve q3 durumu bitiş durumudur, çünkü örnek dizi tamamlandığında bu duruma geçer. Her durum, belirli bir girişten sonra hangi duruma geçileceğini belirtir ve örnek dizi bu durumlar ve geçişler doğrultusunda kabul edilir.

## Kod:

Bu örnekler, farklı durumlar arasındaki geçişleri ve bir otomatın belirli bir dildeki dizileri nasıl tanıyabileceğini göstermektedir. Gösterilen tablolar, belirli bir dilin tanınması için kullanılabilecek temel bir DFA'nın yapılarını sunmaktadır.
