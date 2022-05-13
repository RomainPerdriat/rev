Pour chaque composant qui sera connecté au store, il faudra créer un container. Ce dernier sera le passe plat de la donnée dans mon composant qui sera chargé du rendu.

```js
const InputFormContainer = () => {
  const dispatch = useDispatch();

  const handleSendMessage = (message) => {
    // dispatch l'action pour envoyer le message
    dispatch(
      actionAddMessage(message),
    );
  };

  return (
    <InputForm onSendMessage={handleSendMessage} />
  );
};
```