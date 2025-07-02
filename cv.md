![Anthony](assets/img/self.jpg)

# **Anthony Lou**  

### **Contact Info**  
Email — [tony.ontheroof@gmail.com](mailto:tony.ontheroof@gmail.com)  
Telegram — [@tonyontheroof](https://t.me/tonyontheroof)  
Discord — @an.tony  

---  

### **About Me**  
My goal is to solve problems through code — because it’s fun! My priorities: learning, improving, and building useful things. My strengths include *punctuality* and the *ability to learn quickly*. No professional experience yet, but I’m eager to grow.  

---  

### **Skills**  
- **Version Control**: Git (basic)  
- **Programming**: C (basic), Python (basic), HTML/CSS (basic)  
- **Tools**: Windows, Ubuntu  

---  

### **Code Examples**  
**Conway’s Game of Life** (C)  
A small educational project simulating *Conway’s Game of Life* with random field generation and terminal output.  

```
#include <stdio.h>
#include <stdlib.h>
#include <ncurses.h>
#include <time.h>

int **create_matrix(int rows, int cols);
void free_matrix(int **matrix, int rows);
void draw_matrix(int **matrix, int rows, int cols);
void update_matrix(int **current, int **next, int rows, int cols);
void delay(unsigned long microsec);

int main()
{
    initscr();
    cbreak();
    noecho();
    keypad(stdscr, TRUE);
    nodelay(stdscr, TRUE);

    int rows = 25;
    int cols = 80;

    int **current = create_matrix(rows, cols);
    int **next = create_matrix(rows, cols);

    srand((unsigned int)time(NULL));

    int num_cells = (rows * cols) / 4;
    for (int k = 0; k < num_cells; k++) {
        int i = rand() % rows;
        int j = rand() % cols;
        current[i][j] = 1;
    }

    unsigned long delay_time = 20000000;

    while (1) {
        int ch = getch();
        if (ch == ' ') break;
        if (ch == 'a' || ch == 'A') {
            delay_time -= 1000000;
        }
        if (ch == 'z' || ch == 'Z') {
            delay_time += 1000000;
        }

        draw_matrix(current, rows, cols);
        update_matrix(current, next, rows, cols);

        int **temp = current;
        current = next;
        next = temp;

        delay(delay_time);
    }

    free_matrix(current, rows);
    free_matrix(next, rows);

    endwin();
    return 0;
}

int **create_matrix(int rows, int cols)
{
    int **matrix = malloc(rows * sizeof(int *));
    for (int i = 0; i < rows; i++) {
        matrix[i] = calloc(cols, sizeof(int));
    }
    return matrix;
}

void free_matrix(int **matrix, int rows)
{
    for (int i = 0; i < rows; i++) {
        free(matrix[i]);
    }
    free(matrix);
}

void draw_matrix(int **matrix, int rows, int cols)
{
    clear();
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j]) {
                mvprintw(i, j, "+");
            } else {
                mvprintw(i, j, " ");
            }
        }
    }
    refresh();
}

void update_matrix(int **current, int **next, int rows, int cols)
{
    const int dx[] = {-1, -1, -1, 0, 0, 1, 1, 1};
    const int dy[] = {-1, 0, 1, -1, 1, -1, 0, 1};

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            int neighbors = 0;

            for (int k = 0; k < 8; k++) {
                int ni = (i + dx[k] + rows) % rows;
                int nj = (j + dy[k] + cols) % cols;
                if (current[ni][nj]) {
                    neighbors++;
                }
            }

            if (current[i][j]) {
                if (neighbors < 2 || neighbors > 3) {
                    next[i][j] = 0;
                } else {
                    next[i][j] = 1;
                }
            } else {
                if (neighbors == 3) {
                    next[i][j] = 1;
                } else {
                    next[i][j] = 0;
                }
            }
        }
    }
}

void delay(unsigned long microsec) // instead usleep
{
    volatile unsigned long x = 0;
    while (x < microsec * 10) {
        x++;
    }
}
```

---  

### **Experience**  
**Personal Projects**  
- **[Game of Life Simulator](https://github.com/TonyRoof/school21/blob/main/the_game_of_life)** (C)  
  - Implemented cellular automaton rules with random initialization.  
  - Output visualization via terminal.  
  - *Skills used: C, basic algorithms.* 

---  

### **Education**  
- **School 21** (Intensive Programming Course) – Completed  
- **«Python for Everybody»** – University of Michigan (freeCodeCamp) — In progress

---  

### **Languages**  
**English. Level: B1**  
*Can read documentation, communicate in writing.*
**Russian. Native**