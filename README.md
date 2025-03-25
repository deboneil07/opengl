# OPENGL/GLFW Notes/Guide

## *Compilation Instructions*
`` g++ main.cpp -o opengl_app -lglfw -lGL -lGLEW -lX11 -lpthread -ldl
``

## Table of Contents
1. Window Setup

# Window Setup

``` 
#include <GLFW/glfw3.h>
#include <iostream>

using namespace std;

int main() {
    if (!glfwInit()) {
        fprintf(stderr, "Failed to initialize GLFW\n");
        return -1;
    }

    GLFWwindow* window = glfwCreateWindow(800, 600, "GLFW Test", NULL, NULL);
    if (!window) {
        fprintf(stderr, "Failed to create window\n");
        glfwTerminate();
        return -1;
    }

    glfwMakeContextCurrent(window);

    while (!glfwWindowShouldClose(window)) {
        glClear(GL_COLOR_BUFFER_BIT);
        glfwSwapBuffers(window);
        glfwPollEvents();
    }

    glfwTerminate();
    return 0;
}
```
`` GLFW/glfw3.h -> 	Provides all GLFW functions for window/input management ``

`` iostream ->	C++ standard I/O (used here for error messages) ``

`` glfwInit() -> Initializes GLFW library, returns true on success ``

```
800, 600 ->	Window width/height in pixels
"GLFW Test" ->	Window title bar text
NULL, NULL ->	[Monitor, Share] parameters (null = default)
```
`` glfwMakeContextCurrent() ->	Binds OpenGL to this window
``
```
glfwWindowShouldClose() -> Checks for close requests (X button, etc.)
glClear() -> Clears color buffer to default (black)
glfwSwapBuffers() -> Swaps front/back buffers (double buffering)
glfwPollEvents() ->	Processes input events
```

`` glfwTerminate() ->	Releases all GLFW resources
``