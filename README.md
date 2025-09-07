# WinTermbox
Termbox alternavtive for Windows

## Usage
Clone the repository and compile a dll to link with your project. Or copy the `WinTermbox.h` into your project and define `WINTERMBOX_IMPL` in one of your source files.

## API
```C
/**
 * @brief Enables virtual terminal processing for the console. Must be called before any other function.
 * @return 1 on success, 0 on failure.
 */
extern "C" WINTERMBOX_API int wtb_init(void);

/**
 * @brief Clears the console screen and moves the cursor to the top-left corner.
 * @return 1 on success, 0 when wtb is not initalized.
 */
extern "C" WINTERMBOX_API int wtb_clear(void);

/**
 * @brief Sets the cursor position.
 * @param x The x coordinate (0-based).
 * @param y The y coordinate (0-based).
 * @return 1 on success, 0 when wtb is not initalized.
 */
extern "C" WINTERMBOX_API int wtb_set_cursor_pos(int x, int y);
/**
 * @brief Sets the cursor visibility.
 * @param visibility One of WTB_CURSOR_VISIBILITY_* constants.
 * @return 1 on success, 0 when wtb is not initalized or invalid visibility.
 */
extern "C" WINTERMBOX_API int wtb_set_cursor_visible(int visibility);
/**
 * @brief Sets the cursor shape.
 * @param shape One of WTB_CURSOR_SHAPE_* constants.
 * @return 1 on success, 0 when wtb is not initalized or invalid shape.
 */
extern "C" WINTERMBOX_API int wtb_set_cursor_shape(int shape);
/**
 * @brief Sets a cell at the given position to the given character and colors.
 * @param x The x coordinate (0-based).
 * @param y The y coordinate (0-based).
 * @param ch The character to set.
 * @param fg The foreground color (one of WTB_COLOR_* constants or 0 for default).
 * @param bg The background color (one of WTB_COLOR_* constants or 0 for default).
 * @return 1 on success, 0 when wtb is not initalized or invalid color.
 */
extern "C" WINTERMBOX_API int wtb_set_cell(int x, int y, wchar_t ch, int fg, int bg);
/**
 * @brief Prints a wide string at the given position with the given colors.
 * @param x The x coordinate (0-based).
 * @param y The y coordinate (0-based).
 * @param fg The foreground color (one of WTB_COLOR_* constants or 0 for default).
 * @param bg The background color (one of WTB_COLOR_* constants or 0 for default).
 * @param str The wide string to print.
 * @return 1 on success, 0 when wtb is not initalized or invalid color.
 */
extern "C" WINTERMBOX_API int wtb_wprint(int x, int y, int fg, int bg, const wchar_t* str);

/**
 * @brief Sets the active screen buffer.
 * @param buffer_id One of WTB_SCREEN_BUFFER_* constants.
 * @return 1 on success, 0 when wtb is not initalized or invalid buffer_id.
 */
extern "C" WINTERMBOX_API int wtb_set_screen_buffer(int buffer_id);
/**
 * @brief Sets the default colors for subsequent text output.
 * @param fg The foreground color (one of WTB_COLOR_* constants or 0 for default).
 * @param bg The background color (one of WTB_COLOR_* constants or 0 for default).
 * @return 1 on success, 0 when wtb is not initalized or invalid color.
 */
extern "C" WINTERMBOX_API int wtb_set_color(int fg, int bg);
```
