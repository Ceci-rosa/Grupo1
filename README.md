import React, { useState } from 'react';
import { View, Text, TextInput, Button, StyleSheet } from 'react-native';

export default function App() {
  const [nome, setNome] = useState('');
  const [idade, setIdade] = useState('');
  const [cadastro, setCadastro] = useState(null);
  const [erro, setErro] = useState('');

  function cadastrar() {
  
    if (!nome.trim() || !idade.trim()) {
      setErro('Preencha nome e idade.');
      setCadastro(null);
      return;
    }
    setErro('');
    setCadastro({ nome, idade });
  }

  return (
    <View style={styles.container}>
      <Text style={styles.titulo}>Cadastro</Text>

      <TextInput
        style={styles.input}
        placeholder="Nome"
        value={nome}
        onChangeText={setNome}
      />

      <TextInput
        style={styles.input}
        placeholder="Idade"
        value={idade}
        onChangeText={setIdade}
        keyboardType="numeric"
      />

      <Button title="Cadastrar" onPress={cadastrar} />

      {erro !== '' && <Text style={styles.erro}>{erro}</Text>}

      {cadastro && (
        <Text style={styles.resultado}>
          {cadastro.nome}, {cadastro.idade} anos
        </Text>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, padding: 24, paddingTop: 80, backgroundColor: '#f6f7fb' },
  titulo: { fontSize: 28, fontWeight: 'bold', marginBottom: 24 },
  input: {
    borderWidth: 1,
    borderColor: '#9aa5b8',
    borderRadius: 8,
    padding: 12,
    marginBottom: 16,
    backgroundColor: '#fff',
  },
  erro: { marginTop: 16, color: '#b91c1c', fontSize: 16 },
  resultado: { marginTop: 24, fontSize: 20 },
});
