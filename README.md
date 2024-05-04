import os

def rename_files(directory, pattern):
    # Get list of files in the directory
    files = os.listdir(directory)
    
    # Counter for renamed files
    renamed_count = 0
    
    # Iterate through each file in the directory
    for filename in files:
        # Construct the new filename using the pattern
        new_filename = pattern.format(original=filename)
        
        # Rename the file
        os.rename(os.path.join(directory, filename), os.path.join(directory, new_filename))
        
        # Increment renamed file count
        renamed_count += 1
    
    return renamed_count

def main():
    # Prompt the user to input directory path and naming pattern
    directory = input("Enter the directory path containing the files: ")
    pattern = input("Enter the naming pattern (use '{original}' as placeholder for original filename): ")
    
    # Call the rename_files function
    renamed_count = rename_files(directory, pattern)
    
    # Provide feedback to the user
    print(f"{renamed_count} files renamed successfully.")

if __name__ == "__main__":
    main()
