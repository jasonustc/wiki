# my_libs
### GetFileList
type: ```c/c++```
@return: 0, succeed; -1, failed

```
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
