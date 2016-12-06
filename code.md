# my_libs
### GetFileList
type: ```c/c++```

@brief: get all file list in the current folder

@return: 0, succeed; -1, failed

```c++
int GetFileList(string folderPath, vector<string>& fileList){
	fileList.clear();
	if (!folderPath.empty()){
		namespace fs = boost::filesystem;
		fs::path apk_path(folderPath);
		fs::recursive_directory_iterator end;
		for (fs::recursive_directory_iterator i(apk_path); i != end; ++i){
			const fs::path cp = (*i);
			fileList.push_back(cp.string());
		}
		return 0;
	}
	return -1;
}
```
### CopyFileToFolder
type: ```c/c++```

@brief: copy source file to dest folder

@return: 0

```c++
int CopyFileToFolder(string srcFile, string dstFolder){
	boost::filesystem::create_directory(dstFolder.c_str());
	string fName = srcFile.substr(srcFile.rfind("\\"));
	fName = dstFolder + fName;
	boost::filesystem::path srcPath(srcFile.c_str());
	boost::filesystem::path dstPath(fName.c_str());
	boost::filesystem::copy_file(srcPath, dstPath, boost::filesystem::copy_option::none);
	return 0;
}
```

### GoThroughAllFolders

type ```python```

@brief go through all folders in path

@return folder list

```python
def get_folders_in_path(path):
    folder_list = []
	for parent,dirnames,filenames in os.walk(path):
	    for folder in dirnames:
	        path = os.path.join(parent, folder)
	return folder_list
```
