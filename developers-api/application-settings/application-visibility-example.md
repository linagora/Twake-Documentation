# Display



```text
{
  "tasks_module" : {
    "can_connect_to_tasks": true
	},
  "calendar_module" : {
    "can_connect_to_calendar": true
	}
	"drive_module" : {
    "can_connect_to_directory": true,
    "can_open_files": {
			"url": "", //Une url à appeler pour éditer le fichier (ouvert dans un onglet)
			"preview_url": "", //Une url à appeler pour prévisualiser un fichier (iframe)
			"main_ext": ["docx", "xlsx"], //Extensions principales
			"other_ext": ["txt", "html"] //Extensions secondaires
		},
		"can_create_files": [
			{
				"url": "https://[...]/empty.docx",
				"filename": "Untitled.docx",
				"name": "Word Document"
			},
      {
				"url": "https://[...]/empty.xlsx",
				"filename": "Untitled.xlsx",
				"name": "Excel Document"
			}
		]
  },
  "member_app": true, // Si défini, votre application génèrera un membre
                      // virtuel dans l'espace de travail avec lequel les
                      // utilisateurs pourront discuter.
  "messages_module": {
    "in_plus": {
      "should_wait_for_popup": true
    },
    "right_icon": {
			"icon_url": "", //If defined replace original icon url of your app 
      "should_wait_for_popup": true,
      "type": "file" //"file" | "call"
    },
    "action": {
      "should_wait_for_popup": true,
      "description": "fdsqfds" //Description de l'action, sinon remplacé par le nom de l'app
    },
    "commands": [
			{
				"command": "mycommand", // my_app mycommand
        "description": "fdsqfds"
			}
		]
  },
  "channel": {
    "can_connect_to_channel": ""
  },
  "channel_tab": {
    "iframe": ""
  },
  "app": {
    "iframe": "",
    "plus_btn": {
      "should_wait_for_popup": true
    }
  },
  "configuration": {
    "can_configure_in_workspace": true,
    "can_configure_in_channel": true,
		"can_configure_in_calendar": true,
		"can_configure_in_tasks": true,
    //"can_configure_in_directory": true
  }
}
```

