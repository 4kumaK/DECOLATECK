from docx import Document

# Criando o documento
doc = Document()
doc.add_heading('Desenvolvimento de API REST com Java 17, Spring Boot 3, PostgreSQL, Swagger e Railway', 0)

# Introdução
doc.add_paragraph(
    'Este documento descreve a construção de uma API REST do zero utilizando Java 17, Spring Boot 3, PostgreSQL, Swagger (OpenAPI) e Railway. '
    'O objetivo é criar uma aplicação simples, porém robusta, focada em produtividade e boas práticas de desenvolvimento.'
)

# Passos do Projeto
doc.add_heading('Passos do Projeto', level=1)

# Ambiente de desenvolvimento
doc.add_paragraph(
    '1. **Configuração do Ambiente:**\n'
    '- **Java 17:** Utilizada a versão LTS (Long Term Support) mais recente.\n'
    '- **Spring Boot 3:** Facilita a configuração e implementação da aplicação.\n'
    '- **PostgreSQL:** Banco de dados relacional para persistir os dados da API.\n'
    '- **Spring Data JPA:** Facilita a integração com o banco de dados.\n'
    '- **Swagger/OpenAPI:** Documentação da API.\n'
    '- **Railway:** Plataforma para deploy da aplicação na nuvem.'
)

# Desenvolvimento da API
doc.add_paragraph(
    '2. **Desenvolvendo a API REST com Spring Boot 3:**\n'
    '- **Controller:** Endpoints RESTful (GET, POST, PUT, DELETE) que responderão às requisições HTTP.\n'
    '- **Service Layer:** Contém a lógica de negócio da aplicação.\n'
    '- **Repository Layer:** Utiliza Spring Data JPA para simplificar a interação com o banco de dados.'
)

# Banco de Dados
doc.add_paragraph(
    '3. **Configuração do Banco de Dados:**\n'
    '- **PostgreSQL:** Usado para persistir dados da API.\n'
    '- **Spring Data JPA:** Facilita a integração e as operações CRUD no banco de dados PostgreSQL.'
)

# Documentação com Swagger/OpenAPI
doc.add_paragraph(
    '4. **Documentação da API com Swagger/OpenAPI:**\n'
    '- **OpenAPI/Swagger:** Usado para gerar a documentação interativa da API.\n'
    '- **springdoc-openapi:** Dependência utilizada para integrar o Swagger no projeto.'
)

# Deploy na Nuvem
doc.add_paragraph(
    '5. **Deploy na Nuvem com Railway:**\n'
    '- **Railway:** Plataforma para deployment fácil e rápido. Conecte seu banco de dados PostgreSQL e faça o deploy diretamente na nuvem.'
)

# Exemplos de código
doc.add_heading('Exemplos de Código', level=1)

doc.add_paragraph('1. **Dependências no `pom.xml`:**')
doc.add_paragraph("""
<dependencies>
    <!-- Spring Boot Starter Web -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- Spring Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>

    <!-- PostgreSQL Driver -->
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
    </dependency>

    <!-- Swagger / OpenAPI -->
    <dependency>
        <groupId>org.springdoc</groupId>
        <artifactId>springdoc-openapi-ui</artifactId>
        <version>1.6.9</version>
    </dependency>

    <!-- Spring Boot Starter Test (para testes unitários) -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
""")

doc.add_paragraph('2. **Controller para Endpoints RESTful:**')
doc.add_paragraph("""
@RestController
@RequestMapping("/usuarios")
public class UsuarioController {

    @Autowired
    private UsuarioService usuarioService;

    @GetMapping("/{id}")
    public ResponseEntity<Usuario> getUsuarioById(@PathVariable Long id) {
        return ResponseEntity.ok(usuarioService.getUsuarioById(id));
    }

    @PostMapping
    public ResponseEntity<Usuario> createUsuario(@RequestBody Usuario usuario) {
        return ResponseEntity.status(HttpStatus.CREATED).body(usuarioService.createUsuario(usuario));
    }

    @PutMapping("/{id}")
    public ResponseEntity<Usuario> updateUsuario(@PathVariable Long id, @RequestBody Usuario usuario) {
        return ResponseEntity.ok(usuarioService.updateUsuario(id, usuario));
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteUsuario(@PathVariable Long id) {
        usuarioService.deleteUsuario(id);
        return ResponseEntity.noContent().build();
    }
}
""")

# Conclusão
doc.add_paragraph(
    'Com esses passos, será possível criar uma API RESTful robusta, bem documentada, utilizando Spring Boot 3, PostgreSQL e Swagger/OpenAPI, '
    'facilitando o desenvolvimento e o deploy da aplicação com Railway. A solução criada será escalável e de fácil manutenção, com um foco em '
    'produtividade e boas práticas.'
)

# Salvando o documento
file_path = "/mnt/data/Projeto_API_REST_SpringBoot.docx"
doc.save(file_path)

file_path  # Retornando o caminho para o arquivo gerado.
