Sure, I'll update the script to create the `mvc` directory structure within the `features` directory, specifically tailored for a Flutter project. This structure will include `model`, `view`, and `controller` subdirectories.

Here is the updated script:

```sh
#!/bin/bash

# Function to create a directory if it doesn't already exist and add a description file
create_directory() {
    if [ ! -d "$1" ]; then
        mkdir -p "$1"
        echo "Created directory: $1"
        create_description_file "$1" "$2"
    else
        echo "Directory already exists: $1"
        create_description_file "$1" "$2"
    fi
}

# Function to create a description file within the directory
create_description_file() {
    local dir_path=$1
    local description=$2
    echo "$description" > "$dir_path/description.md"
    echo "Created description file in: $dir_path"
}

# Base directory for the project
BASE_DIR=${1:-.}  # Default to current directory if no argument is provided

# List of directories to create with their descriptions
declare -A DIRECTORIES
DIRECTORIES=(
    ["$BASE_DIR/lib/src/common_widgets"]="Directory for common reusable widgets"
    ["$BASE_DIR/lib/src/constants"]="Directory for constant values used across the project"
    ["$BASE_DIR/lib/src/exceptions"]="Directory for custom exception classes"
    ["$BASE_DIR/lib/src/features"]="Directory for feature-specific code"
    ["$BASE_DIR/lib/src/features/mvc/model"]="Directory for MVC model classes"
    ["$BASE_DIR/lib/src/features/mvc/view"]="Directory for MVC view classes"
    ["$BASE_DIR/lib/src/features/mvc/controller"]="Directory for MVC controller classes"
    ["$BASE_DIR/lib/src/localization"]="Directory for localization files"
    ["$BASE_DIR/lib/src/routing"]="Directory for routing and navigation-related code"
    ["$BASE_DIR/lib/src/utils"]="Directory for utility functions and helpers"
    ["$BASE_DIR/assets/images"]="Directory for image assets"
    ["$BASE_DIR/assets/icons"]="Directory for icon assets"
    ["$BASE_DIR/assets/fonts"]="Directory for font assets"
    ["$BASE_DIR/test"]="Directory for test files"
)

# Create each directory in the list with their descriptions
for DIR in "${!DIRECTORIES[@]}"; do
    create_directory "$DIR" "${DIRECTORIES[$DIR]}"
done

echo "All directories and description files have been created successfully."
```

### Explanation
- **MVC Subdirectories**: The script now includes `model`, `view`, and `controller` subdirectories within the `features` directory.
- **Description Files**: Each directory will have a `description.md` file explaining its purpose.

### Usage
1. Save the script to a file, for example, `create_project_structure_with_mvc.sh`.
2. Make the script executable:
    ```sh
    chmod +x create_project_structure_with_mvc.sh
    ```
3. Run the script with the base directory of your project as an argument:
    ```sh
    ./create_project_structure_with_mvc.sh /path/to/your/project
    ```

This script will create the necessary directories and add a `description.md` file in each one, explaining the purpose of the directory, including the MVC structure within the `features` directory.