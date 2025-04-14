import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Lista de Clientes',
      theme: ThemeData(
        primarySwatch: Colors.grey,
        fontFamily: 'Inter',
      ),
      home: const ClientListPage(),
    );
  }
}

class ClientListPage extends StatelessWidget {
  const ClientListPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.grey[900], // Cor de fundo do Scaffold
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: <Widget>[
            const SizedBox(height: 30), // Espaço do topo
            // Barra de Pesquisa
            Container(
              decoration: BoxDecoration(
                borderRadius: BorderRadius.circular(25), // Raio dos cantos da barra de pesquisa
                color: Colors.grey[800], // Cor da barra de pesquisa
              ),
              child: const TextField(
                decoration: InputDecoration(
                  prefixIcon: Icon(Icons.search, color: Colors.white), // Ícone de pesquisa
                  hintText: 'Pesquisar',
                  hintStyle: TextStyle(color: Colors.white), // Cor do texto de dica
                  border: InputBorder.none, // Remove a borda padrão
                  contentPadding: EdgeInsets.symmetric(vertical: 12, horizontal: 20),
                ),
                style: TextStyle(color: Colors.white), // Cor do texto digitado
              ),
            ),
            const SizedBox(height: 20),
            // Lista de Clientes
            Expanded(
              child: ListView.builder(
                itemCount: 8, // Número de clientes mostrados na imagem
                itemBuilder: (context, index) {
                  return ClientListItem(clientNumber: index + 1);
                },
              ),
            ),
            const SizedBox(height: 20), // Espaço inferior
            // Barra de Ações
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceAround,
              children: [
                IconButton(
                  icon: const Icon(Icons.folder_open, color: Colors.white), // Ícone de pasta
                  onPressed: () {
                    // Ação para abrir a pasta
                  },
                ),
                IconButton(
                  icon: const Icon(Icons.add, color: Colors.white), // Ícone de adição
                  onPressed: () {
                    // Ação para adicionar um novo cliente
                  },
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}

class ClientListItem extends StatelessWidget {
  final int clientNumber;

  const ClientListItem({super.key, required: this.clientNumber});

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: const EdgeInsets.symmetric(vertical: 8),
      padding: const EdgeInsets.all(12),
      decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(15), // Raio dos cantos do item da lista
        color: Colors.grey[800], // Cor do item da lista
      ),
      child: Row(
        mainAxisAlignment: MainAxisAlignment.spaceBetween,
        children: <Widget>[
          Row(
            children: [
              const Icon(Icons.person, color: Colors.blue), // Ícone de pessoa
              const SizedBox(width: 10),
              Text(
                'Client $clientNumber',
                style: const TextStyle(fontSize: 16, color: Colors.white), // Cor do nome do cliente
              ),
            ],
          ),
          ElevatedButton(
            onPressed: () {
              // Ação para fazer o pedido
            },
            style: ElevatedButton.styleFrom(
              backgroundColor: Colors.black, // Cor do botão Pedido
              foregroundColor: Colors.white, // Cor do texto do botão Pedido
              shape: RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(10), // Raio dos cantos do botão Pedido
              ),
            ),
            child: const Text('Pedido'),
          ),
        ],
      ),
    );
  }
}
