#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
};

Node* head = NULL;


void insert(int nilai) {
    Node* baru = new Node();
    baru->data = nilai;
    baru->next = NULL;

    if (head == NULL) {
        head = baru;
    } else {
        Node* temp = head;
        while (temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = baru;
    }
}


void tampil() {
    Node* temp = head;
    while (temp != NULL) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL" << endl;
}


void deleteByValue(int nilai) {
    if (head == NULL) {
        cout << "List kosong\n";
        return;
    }

    Node* temp = head;
    Node* prev = NULL;

    if (temp->data == nilai) {
        head = temp->next;
        delete temp;
        return;
    }


    while (temp != NULL && temp->data != nilai) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL) {
        cout << "Nilai tidak ditemukan\n";
        return;
    }

    prev->next = temp->next;
    delete temp;
}

int main()
{
    int nilaiHapus;

    insert(1);
    insert(2);
    insert(3);
    insert(4);
    insert(5);
    insert(25);

    cout << "Data awal:\n";
    tampil();

    cout << "Masukkan nilai yang ingin dihapus: ";
    cin >> nilaiHapus;

    deleteByValue(nilaiHapus);

    cout << "Setelah dihapus:\n";
    tampil();

    return 0;
}
