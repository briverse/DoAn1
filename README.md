# DoAn1
Đồ án 1 môn KTLT lớp 17CTT7, thầy Phạm Minh Tuấn (học kì 2 năm học 2017 - 2018).

#include <stdio.h>
#include <conio.h>
#include <wchar.h>
#include <stdlib.h>
#include <fcntl.h> //_O_U16TEXT
#include <io.h>    //_setmode()
#include <malloc.h>

const wchar_t* DATA = L"D:/DoAn1/1712920/Demo/Data.csv";

typedef struct STUDENT
{
	char* fullname;
	int id;
	char* faculty;
	char* dob;
	char* email;
	char** hobbies;
	char* description;
	char* image;
} student;

void readFile(FILE* f)
{
	wchar_t c;
	int i = 0;
	while (int(c = fgetwc(f)) != 65535)
	{
		i++;
		wprintf(L"%c", c);
	}

	wprintf(L"\n%d", i);
}


void main()
{
	FILE* file;
	_setmode(_fileno(stdout), _O_WTEXT);
	/*_setmode(_fileno(stdin), _O_WTEXT);*/

	file = _wfopen(DATA, L"r, ccs = UNICODE");
	if (!file)
		wprintf(L"Cannot open this file!\n");
	else
		wprintf(L"The file is opened!\n");

	readFile(file);

	fclose(file);

	_getch();
}
