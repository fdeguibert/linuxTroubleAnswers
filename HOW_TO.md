# run ssh-agent for all sessions

https://stackoverflow.com/questions/18880024/start-ssh-agent-on-login

TL;DR;

Just in case the above link vanishes some day, I am capturing the main piece of the solution below:

This solution from Joseph M. Reagle by way of Daniel Starin:

Add this following to your `.bash_profile`

```SSH_ENV="$HOME/.ssh/environment"

function start_agent {
    echo "Initialising new SSH agent..."
    /usr/bin/ssh-agent | sed 's/^echo/#echo/' > "${SSH_ENV}"
    echo succeeded
    chmod 600 "${SSH_ENV}"
    . "${SSH_ENV}" > /dev/null
    /usr/bin/ssh-add;
}

# Source SSH settings, if applicable

if [ -f "${SSH_ENV}" ]; then
    . "${SSH_ENV}" > /dev/null
    #ps ${SSH_AGENT_PID} doesn't work under cywgin
    ps -ef | grep ${SSH_AGENT_PID} | grep ssh-agent$ > /dev/null || {
        start_agent;
    }
else
    start_agent;
fi```

This version is especially nice since it will see if you've already started ssh-agent and, if it can't find it, will start it up and store the settings so that they'll be usable the next time you start up a shell.
