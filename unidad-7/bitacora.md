# Unidad 7

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 

Código modificado de triangle.cpp , en main()

~~~
#include <glad/glad.h>
#include <GLFW/glfw3.h>
#include <iostream>

// Callback para ajustar el viewport al cambiar tamaño de ventana
void framebuffer_size_callback(GLFWwindow* window, int width, int height) {
    glViewport(0, 0, width, height);
}

// Procesar entrada del teclado
void processInput(GLFWwindow* window, float& offsetX, int& colorMode) {
    if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
        glfwSetWindowShouldClose(window, true);

    if (glfwGetKey(window, GLFW_KEY_RIGHT) == GLFW_PRESS)
        offsetX += 0.01f;
    if (glfwGetKey(window, GLFW_KEY_LEFT) == GLFW_PRESS)
        offsetX -= 0.01f;

    if (glfwGetKey(window, GLFW_KEY_C) == GLFW_PRESS)
        colorMode = 1; // activar color rojo fijo
    if (glfwGetKey(window, GLFW_KEY_V) == GLFW_PRESS)
        colorMode = 0; // volver al color dinámico
}

// Shaders
const char* vertexShaderSource = R"(
#version 330 core
layout (location = 0) in vec3 aPos;

uniform float offsetX;

void main() {
    gl_Position = vec4(aPos.x + offsetX, aPos.y, aPos.z, 1.0);
}
)";

const char* fragmentShaderSource = R"(
#version 330 core
out vec4 FragColor;

uniform float timeValue;
uniform int colorMode;

void main() {
    if (colorMode == 0) {
        // Color dinámico con el tiempo
        float green = (sin(timeValue) / 2.0f) + 0.5f;
        FragColor = vec4(0.0f, green, 1.0f - green, 1.0f);
    } else {
        // Color fijo (rojo)
        FragColor = vec4(1.0f, 0.0f, 0.0f, 1.0f);
    }
}
)";

int main() {
    // Inicializar GLFW
    glfwInit();
    glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
    glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);
    glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);

    // Crear ventana
    GLFWwindow* window = glfwCreateWindow(800, 600, "Triangulo dinamico", NULL, NULL);
    if (window == NULL) {
        std::cout << "Error al crear ventana GLFW" << std::endl;
        glfwTerminate();
        return -1;
    }
    glfwMakeContextCurrent(window);
    glfwSetFramebufferSizeCallback(window, framebuffer_size_callback);

    // Inicializar GLAD
    if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)) {
        std::cout << "Error al inicializar GLAD" << std::endl;
        return -1;
    }

    // Compilar Vertex Shader
    unsigned int vertexShader = glCreateShader(GL_VERTEX_SHADER);
    glShaderSource(vertexShader, 1, &vertexShaderSource, NULL);
    glCompileShader(vertexShader);

    // Compilar Fragment Shader
    unsigned int fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
    glShaderSource(fragmentShader, 1, &fragmentShaderSource, NULL);
    glCompileShader(fragmentShader);

    // Linkear programa
    unsigned int shaderProgram = glCreateProgram();
    glAttachShader(shaderProgram, vertexShader);
    glAttachShader(shaderProgram, fragmentShader);
    glLinkProgram(shaderProgram);

    glDeleteShader(vertexShader);
    glDeleteShader(fragmentShader);

    // Datos del triángulo
    float vertices[] = {
        -0.5f, -0.5f, 0.0f,
         0.5f, -0.5f, 0.0f,
         0.0f,  0.5f, 0.0f
    };

    unsigned int VBO, VAO;
    glGenVertexArrays(1, &VAO);
    glGenBuffers(1, &VBO);

    glBindVertexArray(VAO);

    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
    glEnableVertexAttribArray(0);

    // Loop principal
    float offsetX = 0.0f;
    int colorMode = 0; // 0 = dinámico, 1 = rojo fijo

    while (!glfwWindowShouldClose(window)) {
        // Entrada
        processInput(window, offsetX, colorMode);

        // Render
        glClearColor(0.2f, 0.3f, 0.3f, 1.0f);
        glClear(GL_COLOR_BUFFER_BIT);

        // Activar shader
        glUseProgram(shaderProgram);

        // Uniforms dinámicos
        float timeValue = glfwGetTime();
        int timeLoc = glGetUniformLocation(shaderProgram, "timeValue");
        glUniform1f(timeLoc, timeValue);

        int offsetLoc = glGetUniformLocation(shaderProgram, "offsetX");
        glUniform1f(offsetLoc, offsetX);

        int colorLoc = glGetUniformLocation(shaderProgram, "colorMode");
        glUniform1i(colorLoc, colorMode);

        // Dibujar triángulo
        glBindVertexArray(VAO);
        glDrawArrays(GL_TRIANGLES, 0, 3);

        // Swap buffers y poll events
        glfwSwapBuffers(window);
        glfwPollEvents();
    }

    // Liberar recursos
    glDeleteVertexArrays(1, &VAO);
    glDeleteBuffers(1, &VBO);
    glDeleteProgram(shaderProgram);

    glfwTerminate();
    return 0;
}

~~~








## Bitácora de reflexión
