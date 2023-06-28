# What are the different states a validator can be in?

After a validator is created with a `create-validator` transaction, it can be in three states:

* `bonded`: Validator is in the active set and participates in consensus. Validator is earning rewards and can be slashed for misbehaviour.
* `unbonding`: Validator is not in the active set and does not participate in consensus. Validator is not earning rewards, but can still be slashed for misbehaviour. This is a transition state from `bonded` to `unbonded`. If validator does not send a `rebond` transaction while in `unbonding` mode, it will take three weeks for the state transition to complete.
* `unbonded`: Validator is not in the active set, and therefore not signing blocks. Unbonded validators cannot be slashed, but do not earn any rewards from their operation. It is still possible to delegate UPTICK to this validator. Un-delegating from an `unbonded` validator is immediate.

{% hint style="info" %}
Delegators have the same state as their validator.Delegations are not necessarily bonded. UPTICK can be delegated and bonded, delegated and unbonding, delegated and unbonded, or liquid.
{% endhint %}
