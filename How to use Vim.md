---
quickshare-date: 2024-03-22 21:54:40
quickshare-url: https://noteshare.space/note/clu2s8mrp721101mw9y6x14cn#8V4O53WUE6U13odoqaKrcqv1hnLXbatzCwJr0UQ3Jxw
---

### #Vim commands can be executed two ways:

    - colon command (:q)
    - keybinds (dd)

### Categories of Vim commands:

1. Cursor movement commands:
    - h, j, k, l (move left, down, up, right)
    - w (move to beginning of next word)
    - b (move to beginning of previous word)
    - e (move to end of current word)
    - 0 (move to beginning of line)
    - $ (move to end of line)
    - gg (move to beginning of file)
    - G (move to end of file)
2. Editing commands:
    - i (insert before cursor)
    - a (insert after cursor)
    - o (insert new line below current line)
    - O (insert new line above current line)
    - x (delete character under cursor)
    - dd (delete entire line)
    - y (yank/copy selected text)
    - p (paste copied text)
    - u (undo previous action)
    - . (repeat previous action)
3. Search and replace commands:
    - / (search forward)
    - ? (search backward)
    - :s/old/new/g (replace old with new in current line)
    - :%s/old/new/g (replace old with new in entire file)
4. Navigation commands:
    - :e filename (open a new file)
    - :ls (list open buffers)
    - :b n (switch to buffer with number n)
    - :q (quit Vim) ^784228
    - :w (save changes)
5. Visual commands:
    - v (start visual mode)
    - V (start visual line mode)
    - Ctr-v (start visual block mode)
    - y (copy selected text)
    - p (paste copied text)
    - d (delete selected text)
6. File manipulation commands:
    - :w (save changes)
    - :q (quit Vim)
    - :q! (force quit without saving changes)
    - :wq or :x (save changes and quit)
