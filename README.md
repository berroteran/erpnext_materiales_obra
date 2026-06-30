# Materiales Obra

App Frappe/ERPNext 15 para una pantalla mobile-first de **Solicitud de Materiales** que:

- busca materiales desde `Item`;
- permite seleccionar `Project` y `Cost Center`;
- arma una **lista de materiales solicitados**;
- crea un `Stock Entry` estándar en borrador con tipo `Material Issue`;
- muestra **Mis solicitudes** del usuario autenticado.

## Componentes incluidos

- Ruta web: `/solicitud-materiales`
- Backend whitelisted en `materiales_obra.api`
- Single DocType: `Materiales Obra Settings`
- Bootstrap automático de:
  - rol `Contratista de Obra`
  - custom field en `Item`
  - custom fields en `Stock Entry`

## Instalación en Bench

Requiere que el sitio ya tenga `erpnext` instalado.

```bash
cd /home/frappe/frappe-bench
bench --site <sitio> install-app materiales_obra
bench --site <sitio> migrate
bench build --app materiales_obra
sudo supervisorctl restart all
```

## Configuración mínima

1. Asigne el rol `Contratista de Obra` a los usuarios que usarán el portal.
2. Abra `Materiales Obra Settings`.
3. Configure:
   - `Stock Entry Type`
   - `Bodega de Origen por Defecto` si no desea usar la primera bodega hoja activa
   - `Compañía por Defecto` si el proyecto no define compañía
   - `Item Groups Permitidos`
   - `Item Groups Excluidos`
   - `Exigir flag de Item para el portal` si desea usar el check custom del Item
4. Si activa el flag del Item, marque `Disponible en Portal de Solicitud de Materiales` en los materiales válidos.

## Validación manual sugerida

1. Inicie sesión con un usuario que tenga rol `Contratista de Obra`.
2. Abra `/solicitud-materiales`.
3. Seleccione un `Project` activo y un `Cost Center` hoja.
4. Busque materiales válidos.
5. Agregue cantidades y envíe la solicitud.
6. Verifique que se creó un `Stock Entry` estándar en borrador con tipo `Material Issue`.
7. Revise la sección `Mis solicitudes`.

## License

mit
