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
LocalTime hora = LocalTime.of(9, 5, 12);

// Formatando
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("HH:mm:ss");
String formatada = hora.format(formatter);
System.out.println("Formatada: " + formatada); // 09:05:12

// Convertendo de String para LocalTime
LocalTime convertida = LocalTime.parse("23:45:00", formatter);
System.out.println("Convertida: " + convertida);
```

## Classe `{java} LocalDateTime`

- Representa **data + hora** (ano, mês, dia, hora, minuto, segundo, nanossegundos).
- **Não possui fuso horário** (se precisar, usa-se `ZonedDateTime`).
- É **imutável** e **thread-safe**.
- Muito útil para registros de eventos, logs, timestamps de banco de dados, etc.

### Criando Data e Hora 

```Java
public class ExemploLocalDateTime {
    public static void main(String[] args) {
        // Data e hora atuais
        LocalDateTime agora = LocalDateTime.now();
        System.out.println("Agora: " + agora);
		
        // Data e hora específicas
        LocalDateTime dataHora = LocalDateTime.of(2025, 8, 16, 14, 30, 45);
        System.out.println("Data e hora específicas: " + dataHora);
		
        // A partir de String (formato ISO: yyyy-MM-ddTHH:mm:ss)
        LocalDateTime parseada = LocalDateTime.parse("2025-12-25T10:15:30");
        System.out.println("Parseada: " + parseada);
    }
}
```

### Operações com Data e Hora

```java title:Operações
LocalDateTime agora = LocalDateTime.now();

// Somar / Subtrair tempo
LocalDateTime semanaQueVem = agora.plusWeeks(1);
LocalDateTime ontem = agora.minusDays(1);
LocalDateTime daquiUmaHora = agora.plusHours(1);

// Comparações
boolean antes = agora.isBefore(semanaQueVem); // true
boolean depois = agora.isAfter(ontem);        // true
```

```java title:"Acessando componentes"
LocalDateTime dt = LocalDateTime.of(2025, 8, 16, 22, 15, 45);

int ano = dt.getYear();        // 2025
int mes = dt.getMonthValue();  // 8
int dia = dt.getDayOfMonth();  // 16
int hora = dt.getHour();       // 22
int minuto = dt.getMinute();   // 15
int segundo = dt.getSecond();  // 45
```

```java title:"Formatando data e hora"
LocalDateTime dt = LocalDateTime.of(2025, 8, 16, 9, 5, 12);

// Formatando (padrão customizado)
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");
String formatada = dt.format(formatter);
System.out.println("Formatada: " + formatada); // 16/08/2025 09:05:12

// Convertendo de String para LocalDateTime
LocalDateTime convertida = LocalDateTime.parse("16/08/2025 09:05:12", formatter);
System.out.println("Convertida: " + convertida);
```

### Interoperabilidade
É possível converter entre `LocalDate`, `LocalTime` e `LocalDateTime` facilmente:

```java title:"Convertendo datas e horas"
LocalDate data = LocalDate.now();
LocalTime hora = LocalTime.now();

// Criando LocalDateTime a partir de LocalDate + LocalTime
LocalDateTime dt = LocalDateTime.of(data, hora);

// Extraindo partes
LocalDate soData = dt.toLocalDate();
LocalTime soHora = dt.toLocalTime();
```

