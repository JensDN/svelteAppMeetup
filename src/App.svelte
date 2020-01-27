<script>
    import Header from './UI/Header.svelte'
    import MeetupGrid from './Meetups/MeetupGrid.svelte'
    import TextInput from './UI/TextInput.svelte'
    import Button from './UI/Button.svelte'

    let title ='';
    let subtitle='';
    let address='';
    let email='';
    let description='';
    let imageUrl ='';
    let meetups = [
        {
            id: 'm1',
            title: 'Coding Bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'In this meetup, we will have etc...',
            imageURL: 'https://via.placeholder.com/800x600',
            address: 'placeholder street, placeholder city',
            contactEmail: 'code@test.com'
        },
        {
            id: 'm2',
            title: 'Swimming',
            subtitle: 'Swimming is fun',
            description: 'In this meetup, we will have etc...',
            imageURL: 'https://via.placeholder.com/800x600',
            address: 'placeholder street, placeholder city',
            contactEmail: 'code@test.com'
        }
    ];
    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            contactEmail: email,
            address: address
        };
        meetups =[newMeetup, ...meetups];
    }
</script>
<style>
    #meetups {
        margin-top: 5rem;
    }
    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>
<Header />
<main id="meetups">
    <form on:submit|preventDefault={addMeetup}>
        <TextInput
                id="title"
                label="Title"
                value={title}
                type="text"
                on:input={event => (title= event.target.value)}/>
        <TextInput
                id="subtitle"
                label="Subtitle"
                value={subtitle}
                type="text"
                on:input={event => (subtitle= event.target.value)}/>
        <TextInput
                id="address"
                label="Address"
                value={address}
                type="text"
                on:input={event => (address= event.target.value)}/>

        <TextInput
                id="imageUrl"
                label="Image URL"
                value={imageUrl}
                type="text"
                on:input={event => (imageUrl= event.target.value)}/>
        <TextInput
                id="email"
                label="E-mail"
                value={email}
                type="email"
                on:input={event => (email= event.target.value)}/>
        <TextInput
                id="description"
                label="Description"
                value={description}
                controlType='textarea'
                on:input={event => (description= event.target.value)}/>
        <Button type="submit" caption="Save"/>
    </form>

    <MeetupGrid {meetups}/>
</main>
