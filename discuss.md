# API หน้าตรวจสอบผังรายการ

## 1. ข้อมูลผังย่อย
#### API endpoint: ```get-all-station-schedule-period-playlists-by-id```
#### Method: ```GET```
#### Payload: ```{id: number}``` //period id
#### Response:
```
{
  status: "ok",
  result: {
    id: number,
    period_status_id: number,
    user_id: number,
    name: string,
    icon_path: string,
    period_time_start: string,
    period_time_end: string,
    schedule: {
      id: number,
      schedule_number: string,
      schedule_date: string,
      icon_path: string //ขอเพิ่ม
    },
    station: {
      id: number,
      name: string,
      icon_path: string
    },
    all_playlist: [
      {
        id: number,
        file_name: string,
        file_path: string,
        file_type: string,
        file_size: any,
        icon_path: string,
        time_duration: string,
        station_playlist_status_id: number
      },
      ...
    ],
    modified: Date
  }
}
```
## &nbsp;
## 2. ข้อมูล Playlist
#### API endpoint: ```get-all-station-playlist-comment```
#### Method: ```GET```
#### Payload: ```{id: number}``` //playlist id
#### Response:
```
{
  status: "ok",
  result: {
    id: number,
    comments: {
      id: number,
      name: string,
      description: string,
      created: Date,
      member: { // อาจจะเป็น member หรือ user ก็ได้
        id: number,
        display_name: string,
        avatar_img: string,
        first_name: string,
        last_name: string
      },
      reply_message: [
        {
          id: number,
          name: string,
          description: string,
          created: Date,
          member: {
            id: number,
            display_name: string,
            avatar_img: string,
            first_name: string,
            last_name: string
          },
        },
        ...
      ],
    }, 
    activity: [
      {
        id: number,
        name: string,
        description: string,
        start_time: string,
        created: Date
      },
      ...
    ],
    history: [
      {
        id: number,
        file_name: string,
        file_size: string,
        file_path: string,
        time_duration: string,
        created: Date
      },
      ...
    ]
  }
}
```

## &nbsp;
## 3. ข้อมูลประวัติการพิจารณา
#### API endpoint: ```get-schedule-activity-by-id```
#### Method: ```GET```
#### Payload: ```{id: number}``` //period id
#### Response: 


## &nbsp;
## 4. สร้าง Playlist activity
#### API endpoint: ```create-station-playlist-activity```
#### Method: ```POST```
#### Payload: 
```
{
  station_playlist_id: number,
  description: string,
  start_time: string
}
```
#### Response: 
```
{
  status: "ok",
  message: string
}
```

## &nbsp;
## 5. สร้าง Playlist comment
#### API endpoint: ```create-station-playlist-comment```
#### Method: ```POST```
#### Payload: 
```
{
  station_playlist_id: number,
  description: string,
  reply_id?: number //อาจจะส่งหรือไม่ส่งก็ได้
}
```
#### Response: 
```
{
  status: "ok",
  message: string
}
```
