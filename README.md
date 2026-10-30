 <div align="center">

# ☕ Java — Contact Manager & Data Persistence

**A practical Java project exploring object-oriented programming, collections, object comparison, file handling, and data persistence — written, tested, and documented while learning.**

![Java](https://img.shields.io/badge/Java-OOP%20%26%20File%20Handling-orange?logo=openjdk)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Level](https://img.shields.io/badge/Level-Beginner%20%2F%20Intermediate-blue)

<br>

**· [🇺🇸 English](#-english) · [🇧🇷 Português](#-português) · [🧭 Roadmap](#-learning-roadmap--roteiro-de-estudos) ·**

</div>

---

<details open>
<summary><strong>🇺🇸 English</strong></summary>

### 📖 About

This project is a command-line contact manager developed in Java. It allows users to add, list, search, and remove contacts, while storing information in a text file to preserve data between program executions.

The project combines object-oriented programming, collection management, object comparison, input validation, exception handling, and file persistence.

### 🎯 Topics Covered

- **Classes and Objects:** Creating a `Contato` class to represent individual contacts.
- **Constructors:** Initializing objects with validated name and telephone information.
- **Encapsulation:** Using private attributes and public getters and setters to control access to object data.
- **ArrayList:** Managing a dynamic collection of contacts.
- **Iteration:** Using traditional `for` and enhanced `for-each` loops to traverse and manipulate collections.
- **contains():** Checking whether a contact already exists in the collection.
- **equals():** Overriding object comparison to identify contacts by telephone number.
- **hashCode():** Overriding the hash code method consistently with `equals()`.
- **@Override:** Explicitly indicating methods that redefine inherited behavior.
- **Input Validation:** Checking names and telephone numbers before creating contacts.
- **String Methods:** Using `trim()`, `isEmpty()`, `equalsIgnoreCase()`, `contains()`, and `split()`.
- **File:** Checking whether a file exists before attempting to read it.
- **FileWriter:** Writing contact information to a text file.
- **FileReader:** Opening files for reading.
- **BufferedWriter:** Writing buffered text and using `newLine()` to separate records.
- **BufferedReader:** Reading stored contacts line by line.
- **Try-with-resources:** Automatically closing file resources.
- **IOException:** Handling input/output errors.
- **IllegalArgumentException:** Handling invalid contact information.
- **NumberFormatException:** Handling invalid menu input.
- **Switch and Do-While:** Building an interactive menu that continues until the user chooses to exit.
- **Ternary Operator:** Using conditional expressions to handle potentially null telephone input.
- **Character.isDigit():** Validating telephone numbers character by character.
- **Type Casting:** Converting an `Object` reference into a `Contato` reference during object comparison.

### 💻 Practical Examples

**Comparing contacts using equals()**

```java
@Override
public boolean equals(Object obj) {
    if (this == obj) {
        return true;
    }

    if (!(obj instanceof Contato)) {
        return false;
    }

    Contato outro = (Contato) obj;

    return this.telefone.equals(outro.telefone);
}
```

This implementation considers two contacts equal when they have the same telephone number, regardless of their names.

**Implementing hashCode()**

```java
@Override
public int hashCode() {
    return telefone.hashCode();
}
```

The hash code is based on the same attribute used by `equals()`, maintaining the required consistency between both methods.

**Saving contacts to a file**

```java
try (BufferedWriter escritor =
        new BufferedWriter(new FileWriter(ARQUIVO))) {

    for (Contato contato : contatos) {
        escritor.write(contato.paraArquivo());
        escritor.newLine();
    }

} catch (IOException e) {
    System.out.println("Error: " + e.getMessage());
}
```

Each contact is stored on a separate line using a semicolon as the field separator.

**Loading contacts from a file**

```java
try (BufferedReader leitor =
        new BufferedReader(new FileReader(arquivo))) {

    String linha;

    while ((linha = leitor.readLine()) != null) {
        String[] partes = linha.split(";");

        if (partes.length != 2) {
            continue;
        }

        Contato contato = new Contato(partes[0], partes[1]);

        if (!contatos.contains(contato)) {
            contatos.add(contato);
        }
    }

} catch (IOException e) {
    System.out.println("Error: " + e.getMessage());
}
```

The program reads each record, separates the contact information, validates it through the constructor, and avoids duplicate contacts.

### 🗂️ Project Structure

```text
AgendaContatos/
├── AgendaContatos.java
└── contatos.txt
```

- `AgendaContatos.java`: Contains the interactive menu, contact management operations, file handling, and the `Contato` class.
- `contatos.txt`: Stores contact names and telephone numbers persistently between executions.

### 🧠 Key Concepts

**Object Identity vs. Object Equality**

Two objects can occupy different memory locations and still represent the same logical information.

By overriding `equals()`, the project defines contact equality based on telephone numbers rather than object references.

**equals() and hashCode()**

These methods work together to define object equality and hash-based identification.

When two objects are considered equal through `equals()`, they must return the same hash code. This relationship is essential when working with collections such as `HashSet` and `HashMap`.

**Encapsulation and Validation**

The `Contato` class protects its attributes through private fields and controlled access methods.

The constructor uses setters to ensure that invalid information cannot be assigned during object initialization.

**Memory vs. Persistence**

The `ArrayList` stores contacts in memory while the program is running. The text file preserves this information after the application terminates.

**Data Validation and Exception Handling**

Invalid names, telephone numbers, and menu inputs are handled through validation rules and exception handling, helping prevent incorrect data from entering the application.

**File Reading and Writing**

`BufferedReader` and `BufferedWriter` provide buffered operations for reading and writing information.

The application loads previously saved contacts at startup and writes the current collection to the file when requested or when exiting.

### 🛣️ Learning Roadmap

- [x] Create classes and objects.
- [x] Apply constructors, getters, and setters.
- [x] Use encapsulation and input validation.
- [x] Manage objects with `ArrayList`.
- [x] Iterate through collections using `for` and `for-each`.
- [x] Search and remove objects from a collection.
- [x] Override `equals()` to compare contacts by telephone number.
- [x] Override `hashCode()` consistently with `equals()`.
- [x] Build an interactive menu using `switch` and `do-while`.
- [x] Handle invalid input and exceptions.
- [x] Read and write information using text files.
- [x] Apply try-with-resources.
- [x] Implement data persistence between executions.
- [x] Prevent duplicate contacts during registration and file loading.

</details>

---

<details>
<summary><strong>🇧🇷 Português</strong></summary>

### 📖 Sobre

Este projeto consiste em uma agenda de contatos desenvolvida em Java, executada pelo terminal. Permite adicionar, listar, buscar e remover contatos, armazenando as informações em um arquivo de texto para preservar os dados entre diferentes execuções do programa.

O projeto reúne conceitos de programação orientada a objetos, gerenciamento de coleções, comparação de objetos, validação de entradas, tratamento de exceções e persistência de dados.

### 🎯 Conteúdos Estudados

- **Classes e Objetos:** Criação da classe `Contato` para representar cada contato.
- **Construtores:** Inicialização de objetos com validação de nome e telefone.
- **Encapsulamento:** Utilização de atributos privados e getters e setters públicos para controlar o acesso aos dados.
- **ArrayList:** Gerenciamento de uma coleção dinâmica de contatos.
- **Iteração:** Utilização de laços `for` e `for-each` para percorrer e manipular coleções.
- **contains():** Verificação da existência de um contato na coleção.
- **equals():** Sobrescrita do método de comparação para identificar contatos pelo número de telefone.
- **hashCode():** Sobrescrita do método de código hash de maneira consistente com `equals()`.
- **@Override:** Indicação explícita de métodos que redefinem comportamentos herdados.
- **Validação de Entradas:** Verificação de nomes e telefones antes da criação dos contatos.
- **Métodos de String:** Utilização de `trim()`, `isEmpty()`, `equalsIgnoreCase()`, `contains()` e `split()`.
- **File:** Verificação da existência de um arquivo antes da leitura.
- **FileWriter:** Escrita de informações dos contatos em um arquivo de texto.
- **FileReader:** Abertura de arquivos para leitura.
- **BufferedWriter:** Escrita de texto com buffer e utilização de `newLine()` para separar registros.
- **BufferedReader:** Leitura dos contatos armazenados linha por linha.
- **Try-with-resources:** Fechamento automático dos recursos utilizados.
- **IOException:** Tratamento de erros de entrada e saída.
- **IllegalArgumentException:** Tratamento de informações inválidas dos contatos.
- **NumberFormatException:** Tratamento de entradas inválidas no menu.
- **Switch e Do-While:** Construção de um menu interativo que continua até o usuário escolher sair.
- **Operador Ternário:** Utilização de expressões condicionais para tratar possíveis valores nulos no telefone.
- **Character.isDigit():** Validação dos números de telefone caractere por caractere.
- **Conversão de Tipos:** Conversão de uma referência `Object` para `Contato` durante a comparação de objetos.

### 💻 Exemplos Práticos

**Comparando contatos com equals()**

```java
@Override
public boolean equals(Object obj) {
    if (this == obj) {
        return true;
    }

    if (!(obj instanceof Contato)) {
        return false;
    }

    Contato outro = (Contato) obj;

    return this.telefone.equals(outro.telefone);
}
```

Essa implementação considera dois contatos iguais quando possuem o mesmo número de telefone, independentemente dos nomes.

**Implementando hashCode()**

```java
@Override
public int hashCode() {
    return telefone.hashCode();
}
```

O código hash utiliza o mesmo atributo empregado pelo `equals()`, mantendo a consistência exigida entre os dois métodos.

**Salvando contatos em um arquivo**

```java
try (BufferedWriter escritor =
        new BufferedWriter(new FileWriter(ARQUIVO))) {

    for (Contato contato : contatos) {
        escritor.write(contato.paraArquivo());
        escritor.newLine();
    }

} catch (IOException e) {
    System.out.println("Erro: " + e.getMessage());
}
```

Cada contato é armazenado em uma linha separada, utilizando ponto e vírgula como separador das informações.

**Carregando contatos de um arquivo**

```java
try (BufferedReader leitor =
        new BufferedReader(new FileReader(arquivo))) {

    String linha;

    while ((linha = leitor.readLine()) != null) {
        String[] partes = linha.split(";");

        if (partes.length != 2) {
            continue;
        }

        Contato contato = new Contato(partes[0], partes[1]);

        if (!contatos.contains(contato)) {
            contatos.add(contato);
        }
    }

} catch (IOException e) {
    System.out.println("Erro: " + e.getMessage());
}
```

O programa lê cada registro, separa as informações do contato, valida os dados por meio do construtor e evita contatos duplicados.

### 🗂️ Estrutura do Projeto

```text
AgendaContatos/
├── AgendaContatos.java
└── contatos.txt
```

- `AgendaContatos.java`: Contém o menu interativo, as operações de gerenciamento de contatos, a manipulação de arquivos e a classe `Contato`.
- `contatos.txt`: Armazena nomes e números de telefone de forma persistente entre diferentes execuções.

### 🧠 Conceitos Importantes

**Identidade de Objetos vs. Igualdade de Objetos**

Dois objetos podem ocupar posições diferentes na memória e ainda representar as mesmas informações lógicas.

Ao sobrescrever `equals()`, o projeto define a igualdade entre contatos com base nos números de telefone, em vez de utilizar apenas as referências dos objetos.

**equals() e hashCode()**

Esses métodos trabalham juntos para definir a igualdade e a identificação de objetos em estruturas baseadas em hash.

Quando dois objetos são considerados iguais por `equals()`, obrigatoriamente devem retornar o mesmo código hash. Essa relação é essencial para trabalhar com coleções como `HashSet` e `HashMap`.

**Encapsulamento e Validação**

A classe `Contato` protege seus atributos por meio de campos privados e métodos de acesso controlado.

O construtor utiliza os setters para garantir que informações inválidas não sejam atribuídas durante a inicialização dos objetos.

**Memória vs. Persistência**

O `ArrayList` armazena os contatos na memória enquanto o programa está em execução. O arquivo de texto preserva essas informações mesmo após o encerramento da aplicação.

**Validação de Dados e Tratamento de Exceções**

Nomes, telefones e opções inválidas do menu são tratados por meio de regras de validação e tratamento de exceções, ajudando a impedir que informações incorretas sejam inseridas na aplicação.

**Leitura e Escrita de Arquivos**

`BufferedReader` e `BufferedWriter` oferecem operações com buffer para leitura e escrita de informações.

A aplicação carrega os contatos previamente salvos ao iniciar e grava a coleção atual no arquivo quando solicitado ou durante o encerramento.

### 🛣️ Roadmap

- [x] Criar classes e objetos.
- [x] Aplicar construtores, getters e setters.
- [x] Utilizar encapsulamento e validação de entradas.
- [x] Gerenciar objetos com `ArrayList`.
- [x] Percorrer coleções utilizando `for` e `for-each`.
- [x] Buscar e remover objetos de uma coleção.
- [x] Sobrescrever `equals()` para comparar contatos pelo telefone.
- [x] Sobrescrever `hashCode()` de maneira consistente com `equals()`.
- [x] Construir um menu interativo utilizando `switch` e `do-while`.
- [x] Tratar entradas inválidas e exceções.
- [x] Ler e escrever informações em arquivos de texto.
- [x] Aplicar try-with-resources.
- [x] Implementar persistência de dados entre execuções.
- [x] Impedir contatos duplicados durante o cadastro e o carregamento do arquivo.

</details>

---

<div align="center">

## 🚀 Next Steps

Continue developing the project by exploring more advanced collection structures, such as `HashSet` and `HashMap`, and understanding how hash-based collections use `equals()` and `hashCode()` to identify objects.

Continue desenvolvendo o projeto explorando estruturas de coleções mais avançadas, como `HashSet` e `HashMap`, e compreendendo como coleções baseadas em hash utilizam `equals()` e `hashCode()` para identificar objetos.

## 📚 Repository

Part of the **Java-Learning-Library**, a collection of practical projects documenting the learning process from Java fundamentals to more advanced concepts.

Parte da **Java-Learning-Library**, uma coleção de projetos práticos que documentam o processo de aprendizagem, desde os fundamentos de Java até conceitos mais avançados.

**Made with ☕, curiosity, and consistency.**  
**Feito com ☕, curiosidade e consistência.**

</div>