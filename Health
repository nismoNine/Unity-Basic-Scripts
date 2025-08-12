using UnityEngine;
using UnityEngine.Events;

public class Health : MonoBehaviour
{
    [Header("Health Settings")]
    public float maxHealth = 100f;
    public float currentHealth;

    [Header("Events")]
    public UnityEvent onDamaged;
    public UnityEvent onHealed;
    public UnityEvent onDeath;

    private bool isDead = false;

    void Awake()
    {
        currentHealth = maxHealth;
    }

    public void TakeDamage(float amount)
    {
        if (isDead) return;

        currentHealth -= amount;
        currentHealth = Mathf.Clamp(currentHealth, 0f, maxHealth);

        onDamaged?.Invoke();

        if (currentHealth <= 0f)
            Die();
    }

    public void Heal(float amount)
    {
        if (isDead) return;

        currentHealth += amount;
        currentHealth = Mathf.Clamp(currentHealth, 0f, maxHealth);

        onHealed?.Invoke();
    }

    public void SetHealth(float amount)
    {
        currentHealth = Mathf.Clamp(amount, 0f, maxHealth);
    }

    public void Die()
    {
        if (isDead) return;

        isDead = true;
        onDeath?.Invoke();
        Destroy(gameObject);
    }

    public bool IsDead()
    {
        return isDead;
    }

    public float GetHealthPercent()
    {
        return currentHealth / maxHealth;
    }
