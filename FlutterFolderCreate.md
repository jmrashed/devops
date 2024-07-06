# Flutter Folder Create Shell Script
```bash
#!/bin/bash

# Function to create a directory if it doesn't already exist
create_directory() {
    if [ ! -d "$1" ]; then
        mkdir -p "$1"
        echo "Created directory: $1"
    else
        echo "Directory already exists: $1"
    fi
}

# Base directory for the project
BASE_DIR=${1:-.}  # Default to current directory if no argument is provided

# List of directories to create
DIRECTORIES=(
    "$BASE_DIR/lib/src/common_widgets"
    "$BASE_DIR/lib/src/constants"
    "$BASE_DIR/lib/src/exceptions"
    "$BASE_DIR/lib/src/features"
    "$BASE_DIR/lib/src/localization"
    "$BASE_DIR/lib/src/routing"
    "$BASE_DIR/lib/src/utils"
    "$BASE_DIR/assets/images"
    "$BASE_DIR/assets/icons"
    "$BASE_DIR/assets/fonts"
    "$BASE_DIR/test"
)

# Create each directory in the list
for DIR in "${DIRECTORIES[@]}"; do
    create_directory "$DIR"
done

echo "All directories have been created successfully."
```

