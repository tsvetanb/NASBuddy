## Project
I want to build a NAS based home server. The goal of this application is to provide a user-friendly web-based interface for exploring the contents of the NAS.

## Goals

- Provide a user-friendly web-based interface for exploring the contents of the NAS.
- Privacy: users do not have to use cloud services. All AI features are disabled by default and can run on local machines.

## Features

### Phase 1

- Security: access should be protected by a username and password. Admin users should be able to create new users and assign permissions to them.
- Security: users should be able to change their password.
- Security: permissions should be granted per folders or files with read, write, and delete permissions. Subfolders inherit permissions from their parent folders but can override them.
- File Browser: users should be able to browse the contents of the NAS.
- File Browser: users should be able to upload files to the NAS.
- File Browser: users should be able to download files from the NAS. When multiple files are selected, they should be zipped and downloaded as a single file.
- File Browser: users should be able to delete files from the NAS.
- File Browser: users should be able to create new folders on the NAS.
- File Browser: users should be able to rename files and folders.
- File Browser: users should be able to move files and folders.
- File Browser: users should be able to copy files and folders.
- File Browser: users should be able to search files and folders. There should be a search bar that filters the list of files and folders based on name, date range, and tags.
- File Browser: the searchbar should have a checkbox which enables searching by text contents. When enabled, the search should be performed on the file contents. The application should use the most efficient search tools based on the operating system (e.g. grep)
- File Browser: users should be able to add, edit, and delete tags to files and folders.
- File Browser: users should be able to sort files and folders by name, date, and size.
- File Browser: users should be able to view files and folders in a grid or list view.
- Configuration: admin users should be able to select the folders that are accessible by the users. They should also be able to hide folders from the file browser.
- Image Browser: users should be able to view the contents of the NAS in an image viewer, which should support zooming and panning.
- Image Browser: users should be able to search images based on name, date range, and tags.
- Image Browser: users should be able to add, edit, and delete tags to images.
- Ease of use: the interface should be simple and intuitive. 
- Ease of use: the interface should be responsive and fast. The app should look good on mobile, tablets, and desktops.
- Installation: the app should be easy to install and configure. It should be packaged in a jar file with all dependencies.
- Installation: the app should have sensible defaults and be easy to configure through environment variables or external configuration files.
- Installation: the app should be packaged with default dependencies (like database, tools) and be ready to run.
- Installation: the frontend should be packaged with the app and should automatically start when the app starts.

### Phase 2

- File Browser: users should be able to configure files or folders for versioning. Changes to the files should be tracked and the user should be able to revert to previous versions.
- File Browser: a favorites list should be available, which users can add folders and files to. 
- Image Browser: users should be able to see a map and markers for the images, based on their geolocation.
- API: the app should have a REST API for file and folder management, that can be used by other applications.

### Phase 3

- AI tools: users should be able to use AI tools to process the files and folders. This should include features like OCR, image recognition, and natural language processing.
  - Images should be processed using image recognition tools. Tags should be added to the images based on the recognition results.
    - Images should be processed for face recognition. A repository of known faces should be available. Unknown faces should be marked and users can add them to the repository. Each face can be associated with a name and short description.
    - Image Browser: users should be able to filter images by the faces that are present in them.
  - Text processing: users should be able to process text files using natural language processing tools. Tags should be added to the text files based on the recognition results.
  - Text processing: text files should be processed in a vector space model. Processed entities should reference the file location.
  - File Browser: users should be able to check a checkbox in the search bar and search with natural language.
  - Security: admin users can choose which folders are processed by the AI tools.
  - Configuration: admin users can set up the connection to the AI tools.
  - Configuration: Most modern cloud AI models should be supported (e.g. OpenAI, Anthropic, Cohere, etc.). Local AI models should also be supported.

### Phase 4

- Integrations: the app should be able to integrate with third party services like Google Photos, Dropbox, and other cloud storage services.

## Technical Details

- The backend should be developed with Java and Spring Boot.
- The frontend should be developed with React, TypeScript, and Tailwind CSS.
- Dependent services (like databases) can be managed via Docker.
- All features should be covered by unit tests.