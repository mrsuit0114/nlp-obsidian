<%*
const folderName = await tp.system.prompt("Enter folder name"); // 폴더 이름 입력
const vaultPath = tp.file.folder(); // 현재 볼트의 경로
const folderPath = `${vaultPath}/${folderName}`; // 새 폴더 경로
await app.vault.createFolder(folderPath); // 폴더 생성

// Index 파일 생성
const indexFileName = `${folderPath}/${folderName} Index.md`;
await app.vault.create(indexFileName,'');

// 자동으로 생성된 untitled 파일 삭제
const untitledFilePath = tp.file.path(); // 현재 실행 중인 파일 경로
if (untitledFilePath.includes("Untitled")) {
	await app.vault.delete(tp.file.find(untitledFilePath));
}

// 현재 에러가 난다는 알림이 뜨는데 기능적으로는 정상작동하므로 일단 사용하고 추후 수정
%>
