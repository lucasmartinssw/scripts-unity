# Scripts - Desenvolvimento de Jogos Unity

## Movimento (Horizontal e Vertical)

```csharp
transform.Translate(Input.GetAxis("Horizontal") * velocidade * Time.deltaTime, 0, 0);
transform.Translate(0, Input.GetAxis("Vertical") * velocidade * Time.deltaTime, 0);
```

## Rotacionar

```csharp
transform.Rotate(0, 0, velocidadeRotacao * Time.deltaTime);
```

## Instancionar objetos dinamicamente 

```csharp
public GameObject objeto1;
Instantiate(objeto1, transform.position, transform.rotation);
```

## Destruir outro objeto
```csharp
void OnCollisionEnter2D(Collision2D other)
{
    if (other.gameObject.CompareTag("inimigo"))
    {
        Destroy(other.gameObject);
    }
}
```

## Perseguição (Lógica fantasma do Pacman)
```csharp
public Transform Player;       // Referência ao player
public float velocidade = 3f;   // Velocidade do fantasma
if (Player != null)
    {
        // Move na direção do jogador
        Vector3 direcao = (Player.position - transform.position).normalized;
        transform.position += direcao * velocidade * Time.deltaTime;
    }
```

## Teletransporte (Mudar posição do Player no mesmo cenário)
```csharp
public Transform destino;          // Outro portal
public float cooldown = 0.5f;      // Tempo antes de permitir novo teleporte

private bool podeTeleportar = true;

private void OnTriggerEnter2D(Collider2D col)
    {
        if (col.CompareTag("Player") && podeTeleportar)
        {
            // Teleporta o jogador para o destino
            col.transform.position = destino.position;

            // Inicia cooldown no portal de destino para evitar retorno imediato
            Portal outroPortal = destino.GetComponent<Portal>();
            if (outroPortal != null)
            {
                outroPortal.DesativarTemporariamente(cooldown);
            }
        }
    }

// Desativa o teleporte por um tempo
public void DesativarTemporariamente(float tempo)
{
    podeTeleportar = false;
    Invoke(nameof(ReativarTeleporte), tempo);
}

private void ReativarTeleporte()
{
    podeTeleportar = true;
}

```

### Fechar o editor que roda o jogo 
```csharp
#if UNITY_EDITOR
    UnityEditor.EditorApplication.isPlaying = false;
#endif
```

### Tocar música dinamicamente
```csharp
AudioSource sound = GetComponent<AudioSource>();
if (sound != null)
{
    sound.Play();
}
```

### Trocar de Cena
```csharp
SceneManager.LoadScene("YouWin");
```
