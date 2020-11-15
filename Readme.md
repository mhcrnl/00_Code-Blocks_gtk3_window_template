# Code::Blocks and GTK+3 template window

## Install:
    git clone https://github.com/mhcrnl/00_Code-Blocks_gtk3_window_template.git
    
open with Code::Blocks.
    
## Template:

```
/***************************************************************
    FILE: main.c
    COMPILE:
    gcc `pkg-config --cflags gtk+-3.0` -o MyApp main.c `pkg-config --libs gtk+-3.0`
    AUTHOR: mhcrnl@gmail.com
    SCOPE: Template for GTK3 Code::Blocks
****************************************************************/

#include<gtk/gtk.h>
//************************************************************
static void activate (GtkApplication* app, gpointer user_data)
{
    GtkWidget *window;

    window = gtk_application_window_new(app);
    gtk_window_set_title(GTK_WINDOW(window), "Basic Window");
    gtk_window_set_default_size(GTK_WINDOW(window), 600, 500);
    gtk_widget_show_all(window);
}
//************************************************************
int main (int argc, char **argv)
{
    GtkApplication *app;
    int status;

    app = gtk_application_new ("org.gtk.example", G_APPLICATION_FLAGS_NONE);
    g_signal_connect (app, "activate", G_CALLBACK (activate), NULL);
    status = g_application_run (G_APPLICATION (app), argc, argv);
    g_object_unref(app);

    return status;
}
```