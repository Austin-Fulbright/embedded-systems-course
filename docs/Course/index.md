
### Introduction


This course is for understanding C-programming (as a systems programming language), Embedded Systems, Computer Architecture, Operating Systems, and Computer Graphics, However, the main purpose of this course is to demystifying the ESP-IDF and the ESP32 system hardware from [espressif.](https://www.espressif.com/)

###### Who is this course for?

This course is for people who have a good understanding of embedded systems programming, C and C++ programming, as well as a little bit of knowledge on Computer Graphics.


###### What is this course and why am I making it?

This is a course that will go through the research that I have done to make a course on embedded systems and esp32/esp-idf programming. This course will not use Adruino. 

*(Nothing against Adruino users hopefully this [link](https://spongebob.fandom.com/wiki/Weenie_Hut_Jr%27s) will help get you to the right place.)*

I am making this course for 2 reasons:
1. There is not a lot of good resources for esp-idf other than the official documentation.
2. This will give me motivation to do research on these topics and help me understand them as well.


#### How Can You Help

This course will of course be free :) I am trying to learn and hopefully you will learn with me. The only thing is that I ask for is engagement. Point out what I have wrong, helping me find the correct information, and give me feedback I really want to make this a helpful and reliable resource. I will allow for comment sections on my pages so that people can give feedback and corrections. When I feel comfortable with the information and completeness of this course I will create a video series that I will also make free.

#### Comments On Other Courses

The only good course I have found on esp32 and the esp-idf is [this](https://learnesp32.com/) course here. This course is great and it is a great way to get you started on embedded systems programming on the esp32 board. However, it is missing some information, espeically when it comes to rendering graphics on the [LCD displays](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/lcd/index.html). It also does not contain the optimization features that were added to [esp32-s3](https://www.espressif.com/en/products/socs/esp32-s3), which contain extra registers for specific operations. 

But again this course will also cover a lot of `C`, `C++`, `Computer Architecture`, `Operating Systems`, `Assembly Instructions`, `Embedded Systems`, and `Computer Graphics` So there will be a lot of information that here that I will cover that might have better sources. I will try to link all of my sources that I use and also identify the sources that I think are best for learning more on each topic.



#### Brief Introduction


I am a student who has a passion for the Software Engineering community and learning. I got my undergraduate in computer science from the University of Georgia, and I am currently working on my Masters at Georgia Tech. I have contributed to open source projects and have a passion for maintaining and using open source software whenever I can. I have worked with professional software for about 4 years. I am a bit of a noob when it comes to the professional enviroment but I love learning and hope that I can do and add value to the software engineering community. I also like playing league of legends, but I cant play anymore because of how addicted I get. Here are my op.ggs:

[main](https://www.op.gg/summoners/na/Abotisathot-NA1)

[testing new champs](https://www.op.gg/summoners/na/slinky%20boy-NA1)

[being a degenerate](https://www.op.gg/summoners/na/just%20freaky%20af-NA1)


#### What sets this course apart from others?

This course is a work in progress and will be kind of an open source course. It will try to go in-depth into how the esp-idf works. This course will also contain a lot of practice projects and will be focused on embedded systems programming. So all of the topics we cover like: `C`, `C++`, `Computer Architecture`, `Operating Systems`, `Assembly Instructions`,  and `Computer Graphics` will all be in the context of embedded systems. I will try to find examples in real world projects for each concept we cover that exsists within an embedded system.

For example: Lets say we are learning about buffers in C, I will provide an example of how a buffer in C is used within an embedded system.

```

    ESP_LOGI(TAG, "Initialize RGB LCD panel");
    ESP_ERROR_CHECK(esp_lcd_panel_reset(panel_handle));
    ESP_ERROR_CHECK(esp_lcd_panel_init(panel_handle));

    ESP_LOGI(TAG, "Turn on LCD backlight");
    example_bsp_set_lcd_backlight(EXAMPLE_LCD_BK_LIGHT_ON_LEVEL);

    ESP_LOGI(TAG, "Initialize LVGL library");
    lv_init();
    // create a lvgl display
    lv_display_t *display = lv_display_create(EXAMPLE_LCD_H_RES, EXAMPLE_LCD_V_RES);
    // associate the rgb panel handle to the display
    lv_display_set_user_data(display, panel_handle);
    // set color depth
    lv_display_set_color_format(display, LV_COLOR_FORMAT_RGB565);
    // create draw buffers
    void *buf1 = NULL;
    void *buf2 = NULL;
#if CONFIG_EXAMPLE_DOUBLE_FB
    ESP_LOGI(TAG, "Use frame buffers as LVGL draw buffers");
    ESP_ERROR_CHECK(esp_lcd_rgb_panel_get_frame_buffer(panel_handle, 2, &buf1, &buf2));
    // set LVGL draw buffers and direct mode
    lv_display_set_buffers(display, buf1, buf2, EXAMPLE_LCD_H_RES * EXAMPLE_LCD_V_RES * sizeof(lv_color16_t), LV_DISPLAY_RENDER_MODE_DIRECT);
```
*example from https://github.com/espressif/esp-idf/blob/master/examples/peripherals/lcd/rgb_panel/main/rgb_lcd_example_main.c*

Then I would explain the individual pieces of this code the context and how and why a buffer was used.

This course will also continually update with new technologies and I will always try and document the research that I do on these topics and how they relate to embedded systems programming.



#### What you will need for this course

Its difficult to say what you will need, because it depends on how much of this course you intend to go through. But I will list what you need in order from most important to least important


**hardware requirements:**

1. Computer running: MacOS, Windows 10 | >, Linux
2. esp32 chip
3. esp32s3 chip
4. breadboard
5. ttygo-display-t s3 or regular

Somethings you might want to make sure you are comfortable with:

1. C programming
2. Python
3. Embedded System Basics
4. Networking Basics
5. Operating System Basics
6. GPU and CPU architecture
7. Some familiarity with Assembly

WE WILL NOT USE ADRUINO.

ADRUINO HAS CLUTERRED THE WOLRD WITH ITS ADRUINONESS EVERY SEARCH FOR THESE TOPICS BRINGS UP ADRUINO STUFF





