# Linux-Bash-
codigo el que nos ayuda a conseguir el numero de la especificacion que le pidamos 
#!/bin/bash

LOG_FILE="application.log"

if [ ! -f "$LOG_FILE" ]; then
  echo "Log file '$LOG_FILE' not found."
  exit 1
fi

# List of log levels to track
LOG_LEVELS=("ERROR" "WARN" "INFO" "DEBUG")

for level in "${LOG_LEVELS[@]}"; do
  COUNT=$(grep -c "\b$level\b" "$LOG_FILE")
  if [ "$COUNT" -gt 0 ]; then
    EXAMPLE=$(grep "\b$level\b" "$LOG_FILE" | head -n 1 | sed "s/.*$level //")
    echo "The log contains $COUNT messages of type \"$level\", such as \"$EXAMPLE\"."
  fi
done
