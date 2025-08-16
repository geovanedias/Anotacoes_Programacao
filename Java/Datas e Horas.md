- **Use `LocalDate`** quando quiser **apenas a data**.
- **Use `LocalTime`** para **só hora/minuto/segundo**.
- **Use `LocalDateTime`** quando precisar de **data e hora juntos**.
- **Use `ZonedDateTime`** se precisar levar em conta o **fuso horário**.
- Evite `Date` e `Calendar` em código novo (são legados e menos intuitivos).

## Classe `LocalDate`

- Representa **apenas a data** (ano, mês, dia) — **sem hora e sem fuso horário**.
- É **imutável** e **thread-safe**.
- Faz parte da API moderna (`java.time`) que substitui `Date` e `Calendar`.

### Criando Datas

```java
import java.time.LocalDate;

public class ExemploLocalDate {
    public static void main(String[] args) {
        // Data atual
        LocalDate hoje = LocalDate.now();
        System.out.println("Hoje: " + hoje);
		
        // Data específica (ano, mês, dia)
        LocalDate dataEspecifica = LocalDate.of(2025, 8, 16);
        System.out.println("Data específica: " + dataEspecifica);
		
        // A partir de uma String (formato ISO: yyyy-MM-dd)
        LocalDate parseada = LocalDate.parse("2025-12-25");
        System.out.println("Parseada: " + parseada);
    }
}
```

### Operações com Datas:

```java title:"Verificações"
LocalDate hoje = LocalDate.now();

// Somar/Subtrair dias, meses, anos
LocalDate amanha = hoje.plusDays(1);
LocalDate mesQueVem = hoje.plusMonths(1);
LocalDate anoPassado = hoje.minusYears(1);

// Comparações
boolean antes = hoje.isBefore(amanha); // true
boolean depois = hoje.isAfter(anoPassado); // true
boolean igual = hoje.isEqual(LocalDate.now()); // true
```

```java title:"Acessando componentes"
LocalDate data = LocalDate.of(2025, 8, 16);

int ano = data.getYear();       // 2025
int mes = data.getMonthValue(); // 8
int dia = data.getDayOfMonth(); // 16
```

```java title:"Formatando Datas"
import java.time.format.DateTimeFormatter;

LocalDate data = LocalDate.now();

// Formatando
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
String formatada = data.format(formatter);
System.out.println("Formatada: " + formatada);

// Convertendo de String para LocalDate
LocalDate convertida = LocalDate.parse("16/08/2025", formatter);
System.out.println("Convertida: " + convertida);
```

## Classe ``{java}LocalTime`

- Representa **apenas a hora** (hora, minuto, segundo, nanossegundos).
- Não armazena data nem fuso horário.
- É **imutável** e **thread-safe**.
- Ideal para horários de funcionamento, alarmes, marcação de horas, etc.

### Criando Horas

```java 
import java.time.LocalTime;

public class ExemploLocalTime {
    public static void main(String[] args) {
        // Hora atual do sistema
        LocalTime agora = LocalTime.now();
        System.out.println("Agora: " + agora);
		
        // Hora específica (hora, minuto, segundo)
        LocalTime horaExata = LocalTime.of(14, 30, 0);
        System.out.println("Hora específica: " + horaExata);
		
        // A partir de String (formato ISO: HH:mm[:ss])
        LocalTime parseada = LocalTime.parse("08:45:30");
        System.out.println("Parseada: " + parseada);
    }
}
```

### Operações com Hora:

```java title:Operações
LocalTime agora = LocalTime.now();

// Somar ou subtrair tempo
LocalTime maisUmaHora = agora.plusHours(1);
LocalTime menos30Minutos = agora.minusMinutes(30);

// Comparações
boolean antes = agora.isBefore(maisUmaHora); // true
boolean depois = agora.isAfter(menos30Minutos); // true
```

```java title:"Acessando componentes"
LocalTime hora = LocalTime.of(22, 15, 45);

int h = hora.getHour();       // 22
int m = hora.getMinute();     // 15
int s = hora.getSecond();     // 45
int ns = hora.getNano();      // nanossegundos
```

```java title:"Formatando horários"
import java.time.format.DateTimeFormatter;

LocalTime hora = LocalTime.of(9, 5, 12);

// Formatando
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("HH:mm:ss");
String formatada = hora.format(formatter);
System.out.println("Formatada: " + formatada); // 09:05:12

// Convertendo de String para LocalTime
LocalTime convertida = LocalTime.parse("23:45:00", formatter);
System.out.println("Convertida: " + convertida);
```

