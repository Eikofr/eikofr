
def split_name(name):
    parts = name.split('--')
    return {
        'BamID': parts[0],
        'Ecosystem': parts[1],
        'Env': parts[2]
    }

a = {
    'entityId': 'HOST-008F528F2A958302',
    'type': 'HOST',
    'displayName': 'eurvlii74814.xmp.net.intra',
    'properties': {'detectedName': 'eurvlii74814.xmp.net.intra'},
    'managementzones': [
        {'id': 16586755974723988404, 'name': '11109--OPENSTACK--PRD'},
        {'id': -4077512217512797540, 'name': '11530--KUBE--PRD'},
        {'id': 3127154928271027763, 'name': '11104--EMEAUNIXADMIN--PRD'},
        {'id': 8861840773352861275, 'name': '9427--JENKINS--PRD'}
    ]
}

management_zones = a.pop('managementzones')

new_dicts = []
for zone in management_zones:
    new_dict = a.copy()
    new_dict.update(split_name(zone['name']))
    new_dicts.append(new_dict)

for new_dict in new_dicts:
    print(new_dict)
