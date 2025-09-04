  <modelVersion>4.0.0</modelVersion>
    <groupId>com.ejemplo</groupId>
    <artifactId>inventario-web</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>

    <properties>
        <java.version>17</java.version>
        <spring-boot.version>3.2.5</spring-boot.version>
    </properties>

    <dependencies>
        <!-- Spring Boot Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Thymeleaf (para vistas HTML) -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>

        <!-- DevTools (opcional, recarga automática) -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
package com.ejemplo.inventario;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class InventarioApplication {
    public static void main(String[] args) {
        SpringApplication.run(InventarioApplication.class, args);
    }
}
package com.ejemplo.inventario.model;

import java.util.ArrayList;
import java.util.List;

public class Categoria {
    private String nombre;
    private List<Subcategoria> subcategorias = new ArrayList<>();

    public Categoria(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() { return nombre; }
    public List<Subcategoria> getSubcategorias() { return subcategorias; }

    public void agregarSubcategoria(String nombre) {
        subcategorias.add(new Subcategoria(nombre));
    }
}
package com.ejemplo.inventario.model;

public class Subcategoria {
    private String nombre;

    public Subcategoria(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() { return nombre; }
}
package com.ejemplo.inventario.controller;

import com.ejemplo.inventario.model.Categoria;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;

import java.util.ArrayList;
import java.util.List;

@Controller
public class CategoriaController {
    private List<Categoria> categorias = new ArrayList<>();

    @GetMapping("/")
    public String index() {
        return "index";
    }

    @GetMapping("/categorias")
    public String listarCategorias(Model model) {
        model.addAttribute("categorias", categorias);
        return "categorias";
    }

    @PostMapping("/categorias")
    public String agregarCategoria(@RequestParam String nombre) {
        categorias.add(new Categoria(nombre));
        return "redirect:/categorias";
    }

    @PostMapping("/subcategorias")
    public String agregarSubcategoria(@RequestParam int index, @RequestParam String nombre) {
        if (index >= 0 && index < categorias.size()) {
            categorias.get(index).agregarSubcategoria(nombre);
        }
        return "redirect:/categorias";
    }
}oject xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.ejemplo</groupId>
    <artifactId>inventario-web</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>

    <properties>
        <java.version>17</java.version>
        <spring-boot.version>3.2.5</spring-boot.version>
    </properties>

    <dependencies>
        <!-- Spring Boot Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Thymeleaf (para vistas HTML) -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>

        <!-- DevTools (opcional, recarga automática) -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
package com.ejemplo.inventario;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class InventarioApplication {
    public static void main(String[] args) {
        SpringApplication.run(InventarioApplication.class, args);
    }
}
package com.ejemplo.inventario.model;

import java.util.ArrayList;
import java.util.List;

public class Categoria {
    private String nombre;
    private List<Subcategoria> subcategorias = new ArrayList<>();

    public Categoria(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() { return nombre; }
    public List<Subcategoria> getSubcategorias() { return subcategorias; }

    public void agregarSubcategoria(String nombre) {
        subcategorias.add(new Subcategoria(nombre));
    }
}
package com.ejemplo.inventario.model;

public class Subcategoria {
    private String nombre;

    public Subcategoria(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() { return nombre; }
}
package com.ejemplo.inventario.controller;

import com.ejemplo.inventario.model.Categoria;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;

import java.util.ArrayList;
import java.util.List;

@Controller
public class CategoriaController {
    private List<Categoria> categorias = new ArrayList<>();

    @GetMapping("/")
    public String index() {
        return "index";
    }

    @GetMapping("/categorias")
    public String listarCategorias(Model model) {
        model.addAttribute("categorias", categorias);
        return "categorias";
    }

    @PostMapping("/categorias")
    public String agregarCategoria(@RequestParam String nombre) {
        categorias.add(new Categoria(nombre));
        return "redirect:/categorias";
    }

    @PostMapping("/subcategorias")
    public String agregarSubcategoria(@RequestParam int index, @RequestParam String nombre) {
        if (index >= 0 && index < categorias.size()) {
            categorias.get(index).agregarSubcategoria(nombre);
        }
        return "redirect:/categorias";
    }
}
