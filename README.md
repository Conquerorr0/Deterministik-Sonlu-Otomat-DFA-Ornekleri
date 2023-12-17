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

## Örnek 3: Artan veya Azalan Sayıları Tanıyan Otomat

Bu otomat, belirli kurallara uyan ardışık olarak artan veya azalan sayı dizilerini tanır.

- **Alfabe:** {0, 1, 2, 3, 4, 5, 6, 7, 8, 9} (Sayılar)
- **Durumlar:** {q0, q1, q2}
- **Başlangıç Durumu:** q0
- **Bitiş Durumu:** q2

### Kurallar

- Girişteki sayılar artan bir sırayla ise ("123", "34567", vb.) otomat kabul eder.
- Girişteki sayılar azalan bir sırayla ise ("987", "65432", vb.) otomat kabul eder.
- Aynı sayı birden fazla kez tekrar ederse kabul edilmez ("112", "4554", vb.).

### Durum Geçişleri

| Durumlar       | 0-9 (Giriş)         |
|----------------|---------------------|
| q0 (Başlangıç) | q1 (Artan) veya q2 (Azalan) |
| q1 (Artan)     | q1 (Artan) veya q2 (Azalan) |
| q2 (Azalan)    | q2 (Azalan) veya q1 (Artan) |

Bu otomat, girişteki sayı dizisini inceleyerek ardışık olarak artan veya azalan bir sıra içerip içermediğini kontrol eder. Başlangıç durumu q0'dur ve q2 durumu bitiş durumudur, çünkü artan veya azalan bir sayı dizisini içeren girişleri tanıyan bir otomat olarak tanımlanmıştır.

## Kod:

    import java.util.Scanner;
    
    public class Question3 {
    
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
    
            final STATES FINAL_STATE = STATES.Q2;
            STATES state = STATES.Q0;
    
            System.out.print("Sayı: ");
            String word = scanner.next();
    
            for (int i = 0; i < word.length() - 1; i++) {
                char letter = word.charAt(i);
                char nextLetter = word.charAt(i + 1);
    
                if (letter < '0' || letter > '9') {
                    System.out.println("Hatalı karakter!");
                    System.exit(0);
                }
    
                int num = Character.getNumericValue(letter);
                int nextNum = Character.getNumericValue(nextLetter);
    
                if (state == STATES.Q0) {
                    if (num < nextNum) {
                        state = STATES.Q1;
                    } else if (num > nextNum) {
                        state = STATES.Q2;
                    } 
                    else {
                        System.out.println(word + " otomat tarafından tanınmaz.");
                        System.exit(0);
                    }
                } else if (state == STATES.Q1) {
                    if (num > nextNum) {
                        state = STATES.Q2;
                    } else if (num == nextNum) {
                        System.out.println(word + " otomat tarafından tanınmaz.");
                        System.exit(0);
                    }
                } else {
                    System.out.println(word + " otomat tarafından tanınmaz.");
                    System.exit(0);
                }
            }
    
            if (state == FINAL_STATE || state == STATES.Q1) {
                System.out.println(word + " otomat tarafından tanınır.");
            } else {
                System.out.println(word + " otomat tarafından tanınmaz.");
            }
        }
    }
    
    enum STATES {
        Q0,
        Q1,
        Q2
    }



Bu örnekler, farklı durumlar arasındaki geçişleri ve bir otomatın belirli bir dildeki dizileri nasıl tanıyabileceğini göstermektedir. Gösterilen tablolar, belirli bir dilin tanınması için kullanılabilecek temel bir DFA'nın yapılarını sunmaktadır.
