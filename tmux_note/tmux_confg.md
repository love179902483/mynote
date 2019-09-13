### tmux NOTE

+ First we need to know where is the config file.I put it in `~/.tmux.conf`
+ #### session:
    one session can contain multiple windows,than how to create a session?
    ```
        tmux new -s < name-of-my-session >
    ```
    when you are in one session ,than you can create another session.
    ```
        ctrl b
                :new -s < name-of-my-session >

    ```
    switch from one session to antoher when inner session.

    ```
        ctrl b s
    ```
    get session list outside session.
    ```
        tmux ls
    ```
    enter one session when in terminal
    ```
        tmux attach -t < name-of-my-session >
        or
        tmux a -t < name-of-my-session  >

        # enter the first session in the list
        tmux attach
        or
        tmux a
    ```
    delete session when inner session.
    ```
       ctrl b
       :kill-session

       # delete all sessions
       ctrl b
       :kill-server

    ```
    delete session when outside session.
    ```
        tmux kill-session -t < name-of-my-session >

    ```
+ #### window
    one session can contain multiple windows,and one window can contain multiple panes.

    create window:
    ```
        ctrl-b c

    ```
    view window list
    ```
        ctrl-b w

    ```
    switch to the aim window
    ```
        ctrl-b 0/1/2

    ```
    switch to the next window
    ```
        ctrl-b n

    ```
    switch to the preview window
    ```
        ctrl-b p

    ```
    switch between two windows
    ```
        ctrl-b l

    ```
    rename window
    ```
        ctrl-b ,

    ```
    search keyword
    ```

        ctrl-b f
    ```
    delete window
    ```
        ctrl-b &
    ```
+ #### panes
    one tmux window can slipt multiple panes,and we can move among them.
    
    split pane horizontal
    ```
        ctrl-b "

    ```
    split pane vertical

    ```
        ctrl-b %

    ```
    
    move among panes sequential
    ```
        ctrl-b o

    ```
    move among panes up down left right
    ```
        ctrl-b up down left right
    ```
    resize pane
    ```
    ctrl-b
    :resize-pane -U

    ctrl-b
    :resize-pane -D

    ctrl-b
    :resize-pane -L

    ctrl-b
    :resize-pane -R
    ```
    resize pane ,we can add numbers behind command
    ```
    ctrl-b
    :resize-pane -D 5
    ```
    delete pane
    ```
    ctrl-b x
    ```
    change type setting
    ```
    ctrl-b "space"
    ```
    move pane to new window
    ```
    ctrl-b !
    ```
    move pane to exist window
    ```
    ctrl-b :join-pane -t $window_name
    ```
    move pane as sequential
    ```
    ctrl-b ctrl-o
    ```
    show pane number
    ```
    ctrl-b q
    ```
    show time
    ```
    ctrl-b t
    ```
        
