# useLazyLoading

useLazyLoading is a react hooks that allow users to toggle elements display base on its viewport.

Usage:

Import useLazyLoading from "useLazyLoading" anywhere you need to use it. Remember this is a React Hooks so it should only be use inside React functional components. Apply all of React Hooks rules when using useLazyLoading.

When called useLazyLoading returns an object with to values:
1. show: boolean
2. element: React.ref

Show is a boolean for you to use in your toggle logic regarding when to display your component. If your component is inside the viewport show will be true else false. Please remember to use min-height to the connected component, else they will probably be in the viewport and will be show immediately.

Element is a ref you need to hook to the wrapper of the component you want to toggle.

Example:

    Lets say you have a UserCard component that looks something like this:

    import React from "react"

    const UserCard = ({ img, name, description }) => (
        <div>
            <img src={img} alt={name}>
            <h2>{name}</h2>
            <p>{description}</p>
        </div>
    );

    export default UserCard;

    Now lets implement useLazyLoading hook:

    import React from "react"
    import useLazyLoading from "useLazyLoading"

    const UserCard = ({ img, name, description }) => {
        const {show, element} = useLazyLoading();
        return (
            <div ref={element}>
                {
                    show &&
                    <img src={img} alt={name}>
                    <h2>{name}</h2>
                    <p>{description}</p>
                }
            </div>
        );
    };

    export default UserCard;

    And thats it!!!
