# Resumos

## Atividade 1

What precisely do we mean by software engineering? What distinguishes “software engineering” from “programming” or “computer science”? And why would Google have a unique perspective to add to the corpus of previous software engineering literature written over the past 50 years?

The terms “programming” and “software engineering” have been used interchangeably for quite some time in our industry, although each term has a different emphasis and different implications. University students tend to study computer science and get jobs writing code as “programmers.”

“Software engineering,” however, sounds more serious, as if it implies the application of some theoretical knowledge to build something real and precise. Mechanical engineers, civil engineers, aeronautical engineers, and those in other engineering disciplines all practice engineering. They all work in the real world and use the application of their theoretical knowledge to create something real. Software engineers also create “something real,” though it is less tangible than the things other engineers create.

Unlike those more established engineering professions, current software engineering theory or practice is not nearly as rigorous. Aeronautical engineers must follow rigid guidelines and practices, because errors in their calculations can cause real damage; programming, on the whole, has traditionally not followed such rigorous practices. But, as software becomes more integrated into our lives, we must adopt and rely on more rigorous engineering methods. We hope this book helps others see a path toward more reliable software practices.

### Resumo:
O texto discute o que realmente significa "engenharia de software" e como ela se diferencia de "programação" ou "ciência da computação". Embora esses termos sejam usados como sinônimos, engenharia de software sugere uma aplicação mais séria e estruturada de conhecimento teórico para construir algo real — mesmo que intangível, como o software. Diferente de engenharias tradicionais (como civil ou aeronáutica), a engenharia de software ainda não possui práticas tão rigorosas. No entanto, à medida que o software se torna mais presente em nossas vidas, é necessário adotar métodos mais confiáveis e profissionais. O objetivo do texto (e do livro) é incentivar essa evolução nas práticas da área.

## Atividade 2

Programming Over Time We propose that “software engineering” encompasses not just the act of writing code, but all of the tools and processes an organization uses to build and maintain that code over time. What practices can a software organization introduce that will best keep its code valuable over the long term? How can engineers make a codebase more sustainable and the software engineering discipline itself more rigorous? We don’t have fundamental answers to these questions, but we hope that Google’s collective experience over the past two decades illuminates possible paths toward finding those answers.

One key insight we share in this book is that software engineering can be thought of as “programming integrated over time.” What practices can we introduce to our code to make it sustainable—able to react to necessary change—over its life cycle, from conception to introduction to maintenance to deprecation?

The book emphasizes three fundamental principles that we feel software organizations should keep in mind when designing, architecting, and writing their code:

Time and Change How code will need to adapt over the length of its life

Scale and Growth How an organization will need to adapt as it evolves

Trade-offs and Costs How an organization makes decisions, based on the lessons of Time and Change and Scale and Growth.

### Resumo:
O texto propõe que engenharia de software vai além de apenas programar — ela envolve todos os processos e ferramentas usados para criar e manter o código ao longo do tempo. A ideia central é que engenharia de software pode ser vista como “programação ao longo do tempo”. O objetivo é manter o código sustentável, ou seja, capaz de se adaptar às mudanças durante todo o seu ciclo de vida.

O texto destaca três princípios fundamentais para a construção de software de qualidade:

Tempo e Mudança – Como o código deve evoluir com o tempo.

Escala e Crescimento – Como a organização precisa se adaptar conforme cresce.

Compromissos e Custos – Como tomar decisões equilibradas com base nos dois pontos anteriores.

Embora não ofereça respostas definitivas, o texto busca compartilhar experiências do Google para orientar melhores práticas na área.

## Atividade 3 - Trade off

### Tempo de Entrega vs. Testes Completos
#### Exemplo: 
Lançar um software rapidamente pode atender a uma demanda de mercado urgente, mas sem testes completos, o risco de bugs aumenta.

#### Trade-off: 
Velocidade de entrega vs. confiabilidade do sistema.

### Complexidade do Código vs. Flexibilidade
#### Exemplo: 
Escrever um código mais genérico e flexível permite futuras adaptações, mas pode torná-lo mais difícil de entender e manter.

#### Trade-off: 
Facilidade de manutenção vs. capacidade de adaptação.

### Uso de Bibliotecas Prontas vs. Controle Total
#### Exemplo: 
Utilizar bibliotecas externas acelera o desenvolvimento, mas pode limitar o controle sobre detalhes específicos do funcionamento.

#### Trade-off: 
Rapidez no desenvolvimento vs. controle e personalização.

## Atividade 4 - Resumo e comentário do slide
![bertotiimg](https://github.com/user-attachments/assets/0828d6f2-3849-4e47-8520-a4744932a583)

O slide mostra que, ao desenvolver um sistema complexo, o melhor caminho é começar com uma versão simples e funcional (como um skate), que já resolve o problema do usuário. Com o tempo, ela vai evoluindo até se tornar algo mais completo (como um carro).

### Mensagem principal:

Comece com uma solução que funcione de ponta a ponta, mesmo que simples, em vez de construir partes isoladas que só fazem sentido no final.

## Atividade 5 - Código

### livro.java

```java
package biblioteca;

public class Livro {
    private String titulo;
    private String autor;

    public Livro(String titulo, String autor) {
        this.titulo = titulo;
        this.autor = autor;
    }

    public String getTitulo() {
        return titulo;
    }

    public void setTitulo(String titulo) {
        this.titulo = titulo;
    }

    public String getAutor() {
        return autor;
    }

    public void setAutor(String autor) {
        this.autor = autor;
    }
}
```

### biblioteca.java

```java
package biblioteca;

import java.util.List;
import java.util.LinkedList;

public class Biblioteca {

    private List<Livro> livros = new LinkedList<>();

    public void adicionarLivro(Livro livro) {
        livros.add(livro);
    }

    public Livro buscarPorTitulo(String titulo) {
        for (Livro livro : livros) {
            if (livro.getTitulo().equals(titulo)) {
                return livro;
            }
        }
        return null;
    }

    public List<Livro> buscarPorAutor(String autor) {
        List<Livro> encontrados = new LinkedList<>();
        for (Livro livro : livros) {
            if (livro.getAutor().equals(autor)) {
                encontrados.add(livro);
            }
        }
        return encontrados;
    }

    public List<Livro> getLivros() {
        return livros;
    }
}
```

### teste.java

```java
package biblioteca;

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class Teste {

    @Test
    void testBiblioteca() {
        Biblioteca biblioteca = new Biblioteca();
        biblioteca.adicionarLivro(new Livro("Dom Casmurro", "Machado de Assis"));
        biblioteca.adicionarLivro(new Livro("Memórias Póstumas", "Machado de Assis"));
        biblioteca.adicionarLivro(new Livro("O Cortiço", "Aluísio Azevedo"));

        assertEquals(biblioteca.getLivros().size(), 3);

        Livro livro = biblioteca.buscarPorTitulo("Dom Casmurro");
        assertNotNull(livro);
        assertEquals(livro.getAutor(), "Machado de Assis");

        assertEquals(biblioteca.buscarPorAutor("Machado de Assis").size(), 2);
    }
}
```
